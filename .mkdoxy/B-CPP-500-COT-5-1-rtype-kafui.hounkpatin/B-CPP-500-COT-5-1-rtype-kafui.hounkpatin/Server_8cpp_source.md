

# File Server.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**Server.cpp**](Server_8cpp.md)

[Go to the documentation of this file](Server_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** server
** File description:
** Server
*/

#include "../include/Server.hpp"
Server::Server(boost::asio::io_context &io_context, server_t server_me)
    : room_system(), _game_time_manager(io_context, std::chrono::milliseconds(16))
{
  ThreadPool thread_pool(io_context, std::thread::hardware_concurrency());
  std::thread udp_server_thread([this, &io_context, server_me]()
                                { start_udp_server(io_context, server_me.udp_port); });
  std::thread tcp_server_thread([this, &io_context, server_me]()
                                { start_tcp_server(io_context, server_me.tcp_port); });
  start_heartbeat_monitor(io_context);
  udp_server_thread.join();
  tcp_server_thread.join();
  thread_pool.release();
}

Server::~Server() {}

void Server::run_game()
{
  TimeManager game_timer;
  registry.entity_update();
  movement.enemy_move(registry);
  movement.system_movement(registry.get_entities());
  collision.collison_player_coins(registry);
  collision.collision_player_enemy(registry);
  if (game_timer.getElapsedTimeInSeconds() > 2)
  {
    // send_game_state();
  }
}
void Server::process_message(udp::socket &socket,
                             const std::vector<uint8_t> &buffer,
                             const udp::endpoint &client_endpoint)
{
  // protocol::MessageType type = static_cast<protocol::MessageType>(buffer[0]);

  // switch (type) {
  //     case protocol::MessageType::PLAYER_ACTION: {
  //         protocol::PlayerAction player_action;
  //         if (protocol::deserialize(buffer, player_action)) {
  //             std::cout << "Received Player Action, Player ID: " <<
  //             player_action.player_id
  //                 << ", Action Type: " <<
  //                 static_cast<int>(player_action.action_type) << std::endl;
  //         }
  //         break;
  //     }
  //     case protocol::MessageType::GAME_STATE_UPDATE: {
  //         protocol::GameStateUpdate game_state_update;
  //         if (protocol::deserialize(buffer, game_state_update)) {
  //             std::cout << "Received Game State Update, State Data: ";
  //             for (auto byte : game_state_update.state_data) {
  //                 std::cout << static_cast<int>(byte) << " ";
  //             }
  //             std::cout << std::endl;
  //         }
  //         break;
  //     }
  //     case protocol::MessageType::EVENT_NOTIFICATION: {
  //         protocol::EventNotification event_notification;
  //         if (protocol::deserialize(buffer, event_notification)) {
  //             std::cout << "Received Event Notification, Event Type: " <<
  //             static_cast<int>(event_notification.event_type)
  //                       << std::endl;
  //         }
  //         break;
  //     }
  //     default:
  //         std::cerr << "Unknown message type received." << std::endl;
  //         break;
  // }
  process_message_contain(socket, buffer, client_endpoint);
  check_player_message(socket, buffer, client_endpoint);
}

void Server::handle_tcp_connection(boost::asio::io_context &io_context,
                                   tcp::socket socket)
{
  auto self = std::make_shared<tcp::socket>(std::move(socket));

  auto recv_buffer = std::make_shared<std::vector<uint8_t>>(128);

  self->async_read_some(
      boost::asio::buffer(*recv_buffer),
      [self, recv_buffer](boost::system::error_code ec, std::size_t length)
      {
        if (!ec)
        {
          std::string message(recv_buffer->begin(),
                              recv_buffer->begin() + length);
          std::cout << "Received TCP message: " << message << std::endl;

          std::string response = "ACK";
          boost::asio::async_write(
              *self, boost::asio::buffer(response),
              [self](boost::system::error_code ec, std::size_t)
              {
                if (!ec)
                {
                  std::cout << "Sent TCP acknowledgment" << std::endl;
                }
                else
                {
                  std::cerr
                      << "Error in sending TCP acknowledgment: " << ec.message()
                      << std::endl;
                }
              });
        }
        else
        {
          std::cerr << "Error in reading TCP message: " << ec.message()
                    << std::endl;
        }
      });
}

void Server::start_tcp_server(boost::asio::io_context &io_context, int port)
{
  boost::asio::ip::tcp::acceptor acceptor(
      io_context,
      boost::asio::ip::tcp::endpoint(boost::asio::ip::tcp::v4(), port));
  std::cout << "Server is listening on port: " << port << std::endl;

  boost::asio::ip::tcp::socket socket(io_context);
  acceptor.accept(socket);
  std::cout << "Accepted a connection!" << std::endl;
}

void Server::start_udp_server(boost::asio::io_context &io_context, int port)
{
  try
  {
    udp::socket udp_socket(io_context, udp::endpoint(udp::v4(), port));
    std::cout << "UDP server started on port " << port << std::endl;
    std::array<uint8_t, 128> recv_buffer;
    udp::endpoint remote_endpoint;
    boost::system::error_code error;
    size_t len = 0;
    do
    {
      len = udp_socket.receive_from(boost::asio::buffer(recv_buffer), remote_endpoint, 0, error);
      if (!error && len > 0)
      {
        std::cout << "First client connected from: " << remote_endpoint << std::endl;
        _connected_clients.push_back(remote_endpoint);
      }
    } while (error == boost::asio::error::would_block || len == 0);
    udp_socket.non_blocking(true);
    while (true)
    {
      len = udp_socket.receive_from(boost::asio::buffer(recv_buffer), remote_endpoint, 0, error);
      if (std::find(_connected_clients.begin(), _connected_clients.end(), remote_endpoint) == _connected_clients.end())
      {
        _connected_clients.push_back(remote_endpoint);
        std::cout << "New client connected: " << remote_endpoint << std::endl;
      }
      if (error == boost::asio::error::would_block)
      {
        if (game_run)
        {

          // if (enemyTimer.getElapsedTimeInSeconds() > 7)
          // {
          //   std::cout << "Spawning enemy" << std::endl;
          //   Vector2D pos = registry.spawn_enemy();
          //   std::vector<uint16_t> response = {0x04, enemy_count++, static_cast<uint16_t>(pos.x), static_cast<uint16_t>(pos.y)};
          //   for (auto client : _connected_clients)
          //   {
          //     udp_socket.send_to(boost::asio::buffer(response), client);
          //   }
          //   enemyTimer.restart();
          // }
          // auto enemies = registry.get_entities("Enemy");
          // for (int i = 0; i < enemies.size(); i++)
          // {
          //   enemies[i]->transform->position.x = -5;
          //   std::vector<uint16_t> response = {0x04, static_cast<uint16_t>(i), static_cast<uint16_t>(enemies[i]->transform->position.x), static_cast<uint16_t>(enemies[i]->transform->position.y)};
          //   for (auto client : _connected_clients)
          //   {
          //     udp_socket.send_to(boost::asio::buffer(response), client);
          //   }
          //   response.clear();
          // }
          //movement.enemy_move(registry);
        }
        continue;
      }
      else if (error && error != boost::asio::error::message_size)
      {
        std::cerr << "UDP Receive error: " << error.message() << std::endl;
        break;
      }
      if (len > 0)
      {
        std::vector<uint8_t> data(recv_buffer.begin(), recv_buffer.begin() + len);
        std::thread process_thread([this, &udp_socket, data, remote_endpoint]()
                                   { process_message(udp_socket, data, remote_endpoint); });
        process_thread.detach();
      }
      movement.system_movement(registry.get_entities());
      handle_client_ping(remote_endpoint);
      std::string response = "ACK";
      udp_socket.send_to(boost::asio::buffer(response), remote_endpoint);
      std::cout << "Sent UDP acknowledgment to " << remote_endpoint << std::endl;
    }
  }
  catch (const std::exception &e)
  {
    std::cerr << "UDP Exception: " << e.what() << "\n";
  }
}

// void Server::start_udp_server(boost::asio::io_context &io_context, int port)
// {
//   try
//   {
//     udp::socket udp_socket(io_context, udp::endpoint(udp::v4(), port));
//     std::cout << "UDP server started on port " << port << std::endl;

//     std::array<uint8_t, 128> recv_buffer;
//     udp::endpoint remote_endpoint;
//     udp_socket.non_blocking(true);
//     while (true)
//     {
//       boost::system::error_code error;
//       size_t len = udp_socket.receive_from(boost::asio::buffer(recv_buffer),
//                                            remote_endpoint, 0, error);
//       if (std::find(_connected_clients.begin(), _connected_clients.end(), remote_endpoint) == _connected_clients.end())
//       {
//         _connected_clients.push_back(remote_endpoint);
//       }
//       if (error == boost::asio::error::would_block)
//       {
//         if (game_run)
//         {
//           if (enemyTimer.getElapsedTimeInSeconds() > 2)
//           {
//             std::cout << "Spawning enemy" << std::endl;
//             enemyTimer.restart();
//           }
//         }
//         continue;
//       }
//       else if (error && error != boost::asio::error::message_size)
//       {
//         std::cerr << "UDP Receive error: " << error.message() << std::endl;
//         break;
//       }
//       movement.system_movement(registry.get_entities());
//       auto players = registry.get_entities("Player");
//       std::vector<uint8_t> data(recv_buffer.begin(), recv_buffer.begin() + len);
//       std::thread process_thread([this, &udp_socket, data, remote_endpoint]()
//                                  { process_message(udp_socket, data, remote_endpoint); });
//       process_thread.detach();
//       handle_client_ping(remote_endpoint);
//       std::string response = "ACK";
//       udp_socket.send_to(boost::asio::buffer(response), remote_endpoint);
//       std::cout << "Sent UDP acknowledgment" << std::endl;
//     }
//   }
//   catch (std::exception &e)
//   {
//     std::cerr << "UDP Exception: " << e.what() << "\n";
//   }
// }

int main(int ac, char **av)
{
  server_t server_me;
  if (recup_args(&server_me, ac, av) == false)
  {
    return (84);
  }
  try
  {
    boost::asio::io_context io_context;
    Server server(io_context, server_me);
    io_context.run();
  }
  catch (std::exception &e)
  {
    std::cerr << "Server Exception: " << e.what() << "\n";
  }
}
```


