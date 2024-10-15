

# File Client.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Client.hpp**](Client_8hpp.md)

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
#include <SFML/Graphics.hpp>
#include <SFML/Network.hpp>
#include <SFML/System.hpp>
#include <SFML/Window.hpp>
#include <array>
#include <boost/asio.hpp>
#include <iostream>
#include <thread>
#include <vector>

#include "../../include/Engine/Animation/Animation.hpp"
#include "../../include/Engine/Audio/AudioManager.hpp"
#include "../../include/Engine/Image/ImageManager.hpp"
#include "../../include/Engine/Input/InputManager.hpp"
#include "../../include/Engine/Mouse/MouseManager.hpp"
#include "../../include/Engine/Shape/ShapeManager.hpp"
#include "../Engine/Parallax/parallax.hpp"
#include "Server.hpp"
#include "protocol.hpp"

class Client
{
public:
    Client();
    ~Client();
    void send_tcp_message(const protocol::PlayerAction &message, const std::string &server_ip,
                          int server_port);
    void send_udp_message(const protocol::PlayerAction &message, const std::string &server_ip,
                          int server_port, std::string player_name);

    sf::RenderWindow window;
    sf::Event event;
    boost::asio::io_context _io_context;
    udp::socket _soc;
    udp::endpoint _receiver_endpoint;
    std::vector<sf::RectangleShape> players;
    std::vector<std::pair<int, Animation>> players_id;
    std::vector<sf::CircleShape> enemies;
    std::vector<std::pair<int, Animation>> enemies_id;
    std::vector<sf::CircleShape> projectiles;
    std::vector<std::pair<int, sf::CircleShape>> projectiles_id;
    std::string get_name();
    sf::Font font;
    std::string input;
    ImageManager GamePlayImage, backgroundImage, TeamScoreImage, LifeBoardImage;
    AudioManager ButtonSound;
    Animation player1, player2, enemie1, enemie2, enemie3, enemie4, enemie5, enemie6, enemie7,
        enemie8, enemie9, enemieBoss;
    ShapeManager shapeManager1, shapeManager2;
    TextManager window_manager;
    void create_player_1();
    void create_player_2();
    void create_player_3();
    void create_player_4();
    Animation create_random_enemy(int id);
    std::vector<std::pair<int, std::string>> color_by_enemie;
    std::string get_player_color(int id);
    void assign_enemy();
    std::string get_enemy_color(int id);
    int _health = 100;
    int _score = 0;
    bool game_over = false;

protected:
private:
    int server_tcp_ip;
    int server_udp_ip;
};

#endif /* !CLIENT_HPP_ */
```


