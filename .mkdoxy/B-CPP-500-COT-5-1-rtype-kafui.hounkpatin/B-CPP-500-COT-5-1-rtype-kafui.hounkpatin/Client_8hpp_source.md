

# File Client.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Client.hpp**](Client_8hpp.md)

[Go to the documentation of this file](Client_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** client
** File description:
** Client
*/

#ifndef CLIENT_HPP_
#define CLIENT_HPP_
#include "../include/protocol.hpp"
#include "Server.hpp"
#include <array>
#include <boost/asio.hpp>
#include <iostream>
#include <thread>
#include <vector>
#include <SFML/Network.hpp>
#include <SFML/System.hpp>
#include <SFML/Window.hpp>
#include <SFML/Graphics.hpp>
class Client {
public:
  Client();
  ~Client();
  void send_tcp_message(const protocol::PlayerAction &message,
                        const std::string &server_ip, int server_port);
  void send_udp_message(const protocol::PlayerAction &message,
                        const std::string &server_ip, int server_port);

  sf::RenderWindow window;
  sf::Event event;
  std::vector<sf::RectangleShape> players;
  std::vector<std::pair<int, sf::RectangleShape>> players_id;
  std::vector<sf::CircleShape> enemies;
  std::vector<std::pair<int, sf::CircleShape>> enemies_id;
  std::string get_name();
  void create_player_1();
  void create_player_2();
  void create_player_3();
  void create_player_4();
protected:
private:
  int server_tcp_ip;
  int server_udp_ip;
};

#endif /* !CLIENT_HPP_ */
```


