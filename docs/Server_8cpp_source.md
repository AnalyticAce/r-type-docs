

# File Server.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Server.cpp**](Server_8cpp.md)

[Go to the documentation of this file](Server_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** server
** File description:
** Server
*/

#include "../../include/Server/Server.hpp"

Entity &Server::get_player_entity(const std::string &player_name)
{
    for (auto &entity : registry.get_entities("Player"))
    {
        if (entity->name->name == player_name)
        {
            return *entity;
        }
    }
    throw std::runtime_error("Player not found");
}

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

Server::~Server()
{
}

void Server::process_message(udp::socket &socket, const std::vector<uint8_t> &buffer,
                             const udp::endpoint &client_endpoint)
{
    process_message_contain(socket, buffer, client_endpoint);
    check_player_message(socket, buffer, client_endpoint);
}

void Server::handle_tcp_connection(boost::asio::io_context &io_context, tcp::socket socket)
{
    auto self = std::make_shared<tcp::socket>(std::move(socket));

    auto recv_buffer = std::make_shared<std::vector<uint8_t>>(128);

    self->async_read_some(
        boost::asio::buffer(*recv_buffer),
        [self, recv_buffer](boost::system::error_code ec, std::size_t length)
        {
            if (!ec)
            {
                std::string message(recv_buffer->begin(), recv_buffer->begin() + length);
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
                            std::cerr << "Error in sending TCP acknowledgment: " << ec.message()
                                      << std::endl;
                        }
                    });
            }
            else
            {
                std::cerr << "Error in reading TCP message: " << ec.message() << std::endl;
            }
        });
}

void Server::start_tcp_server(boost::asio::io_context &io_context, int port)
{
    boost::asio::ip::tcp::acceptor acceptor(
        io_context, boost::asio::ip::tcp::endpoint(boost::asio::ip::tcp::v4(), port));
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
            len = udp_socket.receive_from(boost::asio::buffer(recv_buffer), remote_endpoint, 0,
                                          error);
            if (!error && len > 0)
            {
                std::cout << "First client connected from: " << remote_endpoint << std::endl;
                _connected_clients.push_back(remote_endpoint);
            }
        } while (error == boost::asio::error::would_block || len == 0);
        udp_socket.non_blocking(true);
        while (true)
        {
            auto enemies = registry.get_entities("Enemy");
            len = udp_socket.receive_from(boost::asio::buffer(recv_buffer), remote_endpoint, 0,
                                          error);
            if (std::find(_connected_clients.begin(), _connected_clients.end(), remote_endpoint) ==
                _connected_clients.end())
            {
                _connected_clients.push_back(remote_endpoint);
                std::cout << "New client connected: " << remote_endpoint << std::endl;
            }
            if (error == boost::asio::error::would_block)
            {
                if (game_run)
                {
                    if (enemyTimer.getElapsedTimeInSeconds() > 7)
                    {
                        std::cout << "Spawning enemy" << std::endl;
                        Vector2D pos = registry.spawn_enemy();
                        std::vector<uint16_t> response = {0x04, enemy_count++,
                                                          static_cast<uint16_t>(pos.x),
                                                          static_cast<uint16_t>(pos.y)};
                        for (auto client : _connected_clients)
                        {
                            udp_socket.send_to(boost::asio::buffer(response), client);
                        }
                        registry.entity_update();
                        enemyTimer.restart();
                    }
                    if (shootTimer.getElapsedTimeInSeconds() > 5)
                    {
                        std::string name = get_player_name(remote_endpoint);
                        Vector2D pos = shoot.spawn_projectile(registry, get_player_entity(name));
                        std::vector<uint16_t> response = {0x08, projectile_count++,
                                                          static_cast<uint16_t>(pos.x),
                                                          static_cast<uint16_t>(pos.y)};
                        for (auto client : _connected_clients)
                        {
                            udp_socket.send_to(boost::asio::buffer(response), client);
                        }
                        registry.entity_update();
                        shootTimer.restart();
                    }
                    if (coinTimer.getElapsedTimeInSeconds() > 7)
                    {
                        registry.spawn_coin();
                        std::vector<uint16_t> response = {0x010, coin_count++};
                        coinTimer.restart();
                    }
                    for (int i = 0; i < enemies.size(); i++)
                    {
                        if (!enemies[i]->_alive || enemies[i]->transform->position.x < 0)
                        {
                            std::vector<uint16_t> remove_response = {0x09,
                                                                     static_cast<uint16_t>(i)};
                            for (auto &client : _connected_clients)
                            {
                                udp_socket.send_to(boost::asio::buffer(remove_response), client);
                            }
                            enemies[i]->_alive = false;
                            registry.entity_update();
                            std::cout << "Enemy " << i << " died." << std::endl;
                        }
                    }
                    for (auto player : registry.get_entities("Player"))
                    {
                        if (player->health->currentHealth <= 0)
                        {
                            player->_alive = false;
                            int id = get_player_id(remote_endpoint);
                            std::vector<uint16_t> remove_response = {0x011,
                                                                     static_cast<uint16_t>(id)};
                            for (auto &client : _connected_clients)
                            {
                                udp_socket.send_to(boost::asio::buffer(remove_response), client);
                            }

                            std::cout << "Game over." << std::endl;
                        }
                    }
                    if (updateTimer.getElapsedTimeInSeconds() > 0.5)
                    {
                        for (int i = 0; i < enemies.size(); i++)
                        {
                            if (enemies[i] == nullptr || !enemies[i]->_alive)
                            {
                                continue;
                            }
                            enemies[i]->transform->position.x -= 30;
                            if (enemies[i]->transform->position.x <= 2)
                            {
                                std::vector<uint16_t> remove_response = {0x09,
                                                                         static_cast<uint16_t>(i)};
                                for (auto client : _connected_clients)
                                {
                                    udp_socket.send_to(boost::asio::buffer(remove_response),
                                                       client);
                                }
                                enemies[i]->_alive = false;
                                registry.entity_update();
                            }
                            else
                            {
                                std::vector<uint16_t> update_response = {
                                    0x04, static_cast<uint16_t>(i),
                                    static_cast<uint16_t>(enemies[i]->transform->position.x),
                                    static_cast<uint16_t>(enemies[i]->transform->position.y)};
                                std::cout << "Enemy " << i << " position: ("
                                          << enemies[i]->transform->position.x << ", "
                                          << enemies[i]->transform->position.y << ")" << std::endl;
                                for (auto client : _connected_clients)
                                {
                                    udp_socket.send_to(boost::asio::buffer(update_response),
                                                       client);
                                }
                            }
                        }
                        auto projectiles = registry.get_entities("Projectile");
                        for (int i = 0; i < projectiles.size(); i++)
                        {
                            projectiles[i]->transform->position.x += 40;
                            if (projectiles[i]->transform->position.x >= 1366)
                            {
                                projectiles[i]->_alive = false;
                                registry.entity_update();
                            }
                            else
                            {
                                std::vector<uint16_t> update_response = {
                                    0x08, static_cast<uint16_t>(i),
                                    static_cast<uint16_t>(projectiles[i]->transform->position.x),
                                    static_cast<uint16_t>(projectiles[i]->transform->position.y)};
                                for (auto client : _connected_clients)
                                {
                                    udp_socket.send_to(boost::asio::buffer(update_response),
                                                       client);
                                }
                            }
                        }
                        for (auto player : registry.get_entities("Player"))
                        {
                            u_int16_t health = player->health->currentHealth;
                            u_int16_t score = player->score->getScore();
                            int id = get_player_id(remote_endpoint);
                            std::vector<uint16_t> update_response = {0x07, health, score};
                            // if (player->health->currentHealth <= 0)
                            // {
                            //     std::vector<uint16_t> remove_response = {0x011,
                            //                                              static_cast<uint16_t>(id)};
                            //     for (auto client : _connected_clients)
                            //     {
                            //         udp_socket.send_to(boost::asio::buffer(remove_response),
                            //                            client);
                            //     }
                            // }
                            for (auto client : _connected_clients)
                            {
                                udp_socket.send_to(boost::asio::buffer(update_response), client);
                            }
                        }
                        updateTimer.restart();
                    }
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
            collision.collision_player_enemy(registry);
            collision.collision_enemy_projectiles(registry);
            registry.entity_update();
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


