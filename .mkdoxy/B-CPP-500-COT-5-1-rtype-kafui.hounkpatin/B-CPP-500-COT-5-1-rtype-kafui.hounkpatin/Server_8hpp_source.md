

# File Server.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Server.hpp**](Server_8hpp.md)

[Go to the documentation of this file](Server_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** SERVER
** File description:
** Server
*/

#ifndef SERVER_HPP_
#define SERVER_HPP_
#include "../include/protocol.hpp"
#include "ThreadPool.hpp"
#include "room_system.hpp"
#include <array>
#include <boost/asio.hpp>
#include <boost/bind/bind.hpp>
#include <chrono>
#include <cstring>
#include <functional>
#include <iostream>
#include <string>
#include <string_view>
#include <thread>
#include <unordered_map>
#include <vector>
#include "Coin_system.hpp"
#include "Collision_system.hpp"
#include "Entity.hpp"
#include "Health_system.hpp"
#include "Mouvement_system.hpp"
#include "Shoot_system.hpp"
#include "Time_manager.hpp"

using boost::asio::ip::tcp;
using boost::asio::ip::udp;

typedef struct server_me_t {
  int tcp_port;
  int udp_port;
} server_t;

struct parameter_t {
  std::string argument;
  std::function<bool(int *, char **)> add_new_param;
  std::string name;
  std::string usage;
  int check_me;
};

struct EndpointHash {
  std::size_t operator()(const boost::asio::ip::udp::endpoint &endpoint) const {
    return std::hash<std::string>()(endpoint.address().to_string() + ":" +
                                    std::to_string(endpoint.port()));
  }
};

struct EndpointEqual {
  bool operator()(const boost::asio::ip::udp::endpoint &lhs,
                  const boost::asio::ip::udp::endpoint &rhs) const {
    return lhs.address() == rhs.address() && lhs.port() == rhs.port();
  }
};

class Server {
public:
  Server(boost::asio::io_context &io_context, server_t server_me);
  ~Server();
  void process_message(udp::socket &socket, const std::vector<uint8_t> &buffer,
                       const udp::endpoint &client_endpoint);
  void process_message_contain(udp::socket &socket,
                               const std::vector<uint8_t> &buffer,
                               const udp::endpoint &client_endpoint);
  void
  notify_clients_of_disconnection(boost::asio::io_context &io_context,
                                  const udp::endpoint &disconnected_client);
  void check_player_message(udp::socket &socket,
                            const std::vector<uint8_t> &buffer,
                            const udp::endpoint &client_endpoint);
  void start_udp_server(boost::asio::io_context &io_context, int port);
  void handle_tcp_connection(boost::asio::io_context &io_context,
                             tcp::socket socket);
  void start_tcp_server(boost::asio::io_context &io_context, int port);
  void start_heartbeat_monitor(boost::asio::io_context &io_context);
  void handle_client_ping(const udp::endpoint &client_endpoint);
  void send_udp_with_ack(udp::socket &socket,
                         const std::vector<uint8_t> &message,
                         const udp::endpoint &client_endpoint);

  void handle_room_creation(udp::socket &socket, const std::string &room_name,
                            const udp::endpoint &client_endpoint);
  void handle_room_joining(udp::socket &socket, int room_id,
                           const udp::endpoint &client_endpoint);
  void handle_list_rooms(udp::socket &socket,
                         const udp::endpoint &client_endpoint);
  
  std::vector<std::pair<udp::endpoint, std::string>> id_name;
  void run_game();
  boost::asio::steady_timer _game_time_manager;
  Registry registry;
  MouvementSystem movement;
  TimeManager enemyTimer;
  CollisionSystem collision;
  bool game_run = false;
  u_int16_t players_count = 0;
  u_int16_t enemy_count = 0;
  std::vector<udp::endpoint> _connected_clients;
  int get_player_id(const udp::endpoint &client_endpoint);
  void check_player_position(udp::socket &socket,
                             const std::vector<uint8_t> &buffer,
                             const udp::endpoint &client_endpoint);
protected:
private:
  struct ClientInfo {
    std::chrono::steady_clock::time_point last_ping;
  };
  std::unordered_map<udp::endpoint, ClientInfo, EndpointHash, EndpointEqual>
      clients_me;
  std::unordered_map<udp::endpoint, std::string, EndpointHash, EndpointEqual>
      clients;
  Room_System room_system;
};

bool recup_args(server_t *server, int ac, char **av);

#endif /* !SERVER_HPP_ */
```


