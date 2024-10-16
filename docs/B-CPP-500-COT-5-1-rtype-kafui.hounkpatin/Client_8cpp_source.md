

# File Client.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Client.cpp**](Client_8cpp.md)

[Go to the documentation of this file](Client_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** client
** File description:
** Client
*/

#include "../../include/Server/Client.hpp"

using boost::asio::ip::tcp;
using boost::asio::ip::udp;

Client::Client() : _io_context(), _soc(_io_context)
{
}
void Client::send_tcp_message(const protocol::PlayerAction &message, const std::string &server_ip,
                              int server_port)
{
    try
    {
        boost::asio::io_context io_context;
        tcp::resolver resolver(io_context);
        tcp::resolver::query query(tcp::v4(), server_ip, std::to_string(server_port));
        tcp::resolver::iterator endpoint_iterator = resolver.resolve(query);
        tcp::socket socket(io_context);
        boost::asio::connect(socket, endpoint_iterator);

        while (true)
        {
            auto buffer = protocol::serialize(message);
            boost::asio::write(socket, boost::asio::buffer(buffer));
            std::cout << "TCP message sent" << std::endl;
            std::vector<uint8_t> recv_buffer(128);
            boost::system::error_code error;
            size_t len = socket.read_some(boost::asio::buffer(recv_buffer), error);
            if (error)
            {
                std::cerr << "TCP Exception: " << error.message() << "\n";
                if (error == boost::asio::error::eof)
                {
                    std::cout << "Connection closed by the server." << std::endl;
                    break;
                }
                else if (error == boost::asio::error::connection_reset)
                {
                    std::cout << "Connection reset by peer." << std::endl;
                    break;
                }
                else if (error == boost::asio::error::operation_aborted)
                {
                    std::cout << "Operation aborted." << std::endl;
                    break;
                }
                else
                {
                    throw boost::system::system_error(error);
                }
            }

            std::cout << "Received TCP acknowledgment, length: " << len << std::endl;
            if (len > 0)
            {
                std::string response(recv_buffer.begin(), recv_buffer.begin() + len);
                std::cout << "Received TCP acknowledgment: " << response << std::endl;
            }

            std::this_thread::sleep_for(std::chrono::seconds(5));
        }
    }
    catch (std::exception &e)
    {
        std::cerr << "TCP Exception: " << e.what() << "\n";
    }
}

std::string Client::get_name()
{
    sf::RenderWindow window(sf::VideoMode(400, 200), "Player Name Entry");

    sf::Font font;
    if (!font.loadFromFile("04B_19__.TTF"))
    {
        std::cerr << "Failed to load font\n";
        exit(84);
    }
    std::string _name;
    sf::Text text;
    text.setFont(font);
    text.setCharacterSize(24);
    text.setFillColor(sf::Color::Black);
    text.setPosition(10.f, 10.f);
    text.setString("Enter player name:");

    sf::Text playerNameText;
    playerNameText.setFont(font);
    playerNameText.setCharacterSize(24);
    playerNameText.setFillColor(sf::Color::Black);
    playerNameText.setPosition(10.f, 50.f);

    bool enteringName = true;
    _name.clear();
    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
            {
                window.close();
            }
            else if (event.type == sf::Event::TextEntered && enteringName)
            {
                if (event.text.unicode == '\b' && !_name.empty())
                {
                    _name.erase(_name.size() - 1);
                }
                else if (event.text.unicode < 128 && _name.size() < 20)
                {
                    _name += event.text.unicode;
                }
                playerNameText.setString(_name);
            }
            else if (event.type == sf::Event::KeyPressed && event.key.code == sf::Keyboard::Return)
            {
                if (_name.empty())
                    _name = "Anonymous";
                enteringName = false;
                window.close();
                return _name;
            }
        }
        window.clear(sf::Color::White);
        window.draw(text);
        window.draw(playerNameText);
        window.display();
    }

    delete &window;
    return _name;
}

void Client::create_player_1()
{
    sf::RectangleShape player(sf::Vector2f(50, 50));
    player.setFillColor(sf::Color::Transparent);
    player.setOutlineColor(sf::Color::Red);
    player.setPosition(100, 100);
    players.push_back(player);
    player1.loadAnimation("red", 8, 1.5, 1.5);
    players_id.push_back(std::make_pair(1, player1));
}

void Client::create_player_2()
{
    sf::RectangleShape player(sf::Vector2f(50, 50));
    player.setFillColor(sf::Color::Yellow);
    player.setPosition(100, 300);
    players.push_back(player);
    player2.loadAnimation("blue", 8, 1.5, 1.5);
    player2.setPosition("blue", 100, 200);
    players_id.push_back(std::make_pair(2, player2));
}

std::string Client::get_player_color(int id)
{
    if (id == 1)
        return "red";
    else if (id == 2)
        return "blue";
    else
        return "red";
}

Animation Client::create_random_enemy(int id)
{

    int random = rand() % 9 + 1;
    if (random == 1)
    {
        enemie1.loadAnimation("green", 8, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "green"));
        return enemie1;
    }
    else if (random == 2)
    {
        enemie2.loadAnimation("yellow", 8, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "yellow"));
        return enemie2;
    }
    else if (random == 3)
    {
        enemie3.loadAnimation("purple", 8, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "purple"));
        return enemie3;
    }
    else if (random == 4)
    {
        enemie4.loadAnimation("orange", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "orange"));
        return enemie4;
    }
    else if (random == 5)
    {
        enemie5.loadAnimation("pink", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "pink"));
        return enemie5;
    }
    else if (random == 6)
    {
        enemie6.loadAnimation("cyan", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "cyan"));
        return enemie6;
    }
    else if (random == 7)
    {
        enemie7.loadAnimation("brown", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "brown"));
        return enemie7;
    }
    else if (random == 8)
    {
        enemie8.loadAnimation("white", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "white"));
        return enemie8;
    }
    else if (random == 9)
    {
        enemie9.loadAnimation("black", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "black"));
        return enemie9;
    }
    else
    {
        enemie1.loadAnimation("green", 5, 1.25, 1.25);
        color_by_enemie.push_back(std::make_pair(id, "green"));
        return enemie1;
    }
}

std::string Client::get_enemy_color(int id)
{
    for (auto &color : color_by_enemie)
    {
        if (color.first == id)
        {
            return color.second;
        }
    }
    return "green";
}

void Client::send_udp_message(const protocol::PlayerAction &message, const std::string &server_ip,
                              int server_port, std::string player_name)
{
    Parallax parallax("assets/image/Background/background1.png",
                      "assets/image/Background/background1.png", 50.f, 50.f);
    window_manager.loadFont("assets/font/04B_19__.TTF");
    sf::Clock clock;
    try
    {
        // boost::asio::io_context io_context;
        udp::resolver resolver(_io_context);
        udp::resolver::query query(udp::v4(), server_ip, std::to_string(server_port));
        _receiver_endpoint = *resolver.resolve(query).begin();

        _soc = udp::socket(_io_context);
        _soc.open(udp::v4());
        _soc.non_blocking(true);
        uint8_t connect_message = 0x01;
        _soc.send_to(boost::asio::buffer(&connect_message, 1), _receiver_endpoint);
        std::cout << "Sent player connection request" << std::endl;

        // std::string player_name = get_name();
        int nb_players = 0;
        uint8_t name_message[21] = {0x02};
        for (int i = 0; i < player_name.size(); i++)
        {
            name_message[i + 1] = player_name[i];
        }
        _soc.send_to(boost::asio::buffer(name_message, 21), _receiver_endpoint);
        std::cout << "Sent player name: " << player_name << std::endl;

        window.create(sf::VideoMode(1366, 768), "SFML window");

        while (window.isOpen())
        {
            while (window.pollEvent(event))
            {
                if (event.type == sf::Event::Closed)
                {
                    players.clear();
                    window.close();
                }
                if (event.type == sf::Event::KeyPressed)
                {
                    if (sf::Keyboard::isKeyPressed(sf::Keyboard::Up))
                    {
                        uint8_t move_message[2] = {0x03, 0x01};
                        _soc.send_to(boost::asio::buffer(move_message, 2), _receiver_endpoint);
                        std::cout << "Sent player movement: keyup" << std::endl;
                    }
                    if (sf::Keyboard::isKeyPressed(sf::Keyboard::Down))
                    {
                        uint8_t move_message[2] = {0x03, 0x02};
                        _soc.send_to(boost::asio::buffer(move_message, 2), _receiver_endpoint);
                        std::cout << "Sent player movement: keydown" << std::endl;
                    }
                    if (sf::Keyboard::isKeyPressed(sf::Keyboard::Left))
                    {
                        uint8_t move_message[2] = {0x03, 0x03};
                        _soc.send_to(boost::asio::buffer(move_message, 2), _receiver_endpoint);
                        std::cout << "Sent player movement: keyleft" << std::endl;
                    }
                    if (sf::Keyboard::isKeyPressed(sf::Keyboard::Right))
                    {
                        uint8_t move_message[2] = {0x03, 0x04};
                        _soc.send_to(boost::asio::buffer(move_message, 2), _receiver_endpoint);
                        std::cout << "Sent player movement: keyright" << std::endl;
                    }
                }
            }
            window.clear();
            std::array<u_int16_t, 128> recv_buffer;
            udp::endpoint sender_endpoint;
            boost::system::error_code error;
            size_t len =
                _soc.receive_from(boost::asio::buffer(recv_buffer), sender_endpoint, 0, error);

            if (error == boost::asio::error::would_block)
            {
                continue;
            }
            else if (error)
            {
                std::cerr << "UDP Exception: " << error.message() << "\n";
                break;
            }
            if (len > 0)
            {
                if (recv_buffer[0] == 0x03)
                {
                    std::cout << "Received UDP acknowledgment data: " << recv_buffer.data()
                              << std::endl;
                    int id = recv_buffer[1];
                    float pos_x = static_cast<float>(recv_buffer[2]);
                    float pos_y = static_cast<float>(recv_buffer[3]);

                    if (id == 1)
                    {
                        player1.setPosition("red", pos_x, pos_y);
                    }
                    else if (id == 2)
                    {
                        player2.setPosition("blue", pos_x, pos_y);
                    }
                    else
                    {
                        return;
                    }
                }
                if (recv_buffer[0] == 0x02)
                {
                    nb_players = recv_buffer[1];
                    std::cout << "Received UDP acknowledgment data: " << recv_buffer.data()
                              << std::endl;
                    std::cout << "Players size : " << nb_players << std::endl;
                    if (nb_players >= 1 && players_id.size() == 0)
                    {
                        create_player_1();
                    }
                    if (nb_players >= 2 && players_id.size() == 1)
                    {
                        create_player_2();
                    }
                    // if (nb_players >= 3 && players_id.size() == 2)
                    // {
                    //     create_player_3();
                    // }
                    // if (nb_players >= 4 && players_id.size() == 3)
                    // {
                    //     create_player_4();
                    // }
                    std::cout << "Received updated game state" << std::endl;
                }
                if (recv_buffer[0] == 0x04)
                {
                    int v = 0;
                    int id = recv_buffer[1];
                    int pos_x = recv_buffer[2];
                    int pos_y = recv_buffer[3];
                    for (auto &enemy : enemies_id)
                    {
                        if (enemy.first == id)
                        {
                            std::string color = get_enemy_color(id);
                            enemy.second.setPosition(color, pos_x, pos_y);
                            std::cout << "Updated enemy " << id << " position to: (" << pos_x
                                      << ", " << pos_y << ")" << std::endl;
                            v = 1;
                            window.clear();
                        }
                    }
                    if (v == 0)
                    {
                        Animation enemy = create_random_enemy(id);
                        enemies_id.push_back(std::make_pair(id, enemy));
                    }
                }
                if (recv_buffer[0] == 0x05)
                {
                    int id = recv_buffer[1];
                    float pos_x = static_cast<float>(recv_buffer[2]);
                    float pos_y = static_cast<float>(recv_buffer[3]);
                    std::cout << "Received player id :" << id << "position: (" << pos_x << ", "
                              << pos_y << ")" << std::endl;
                    for (int i = 0; i < players_id.size(); i++)
                    {
                        if (players_id[i].first == id)
                        {
                            players_id[i].second.setPosition(get_player_color(id), pos_x, pos_y);
                        }
                    }
                }
                if (recv_buffer[0] == 0x08)
                {
                    int id = recv_buffer[1];
                    int pos_x = recv_buffer[2];
                    int pos_y = recv_buffer[3];
                    int v = 0;
                    for (auto &projectile : projectiles_id)
                    {
                        if (projectile.first == id)
                        {
                            std::cout << "Updated projectile " << id << " position to: (" << pos_x
                                      << ", " << pos_y << ")" << std::endl;
                            projectile.second.setPosition(pos_x, pos_y);
                            v = 1;
                            window.clear();
                        }
                    }
                    if (v == 0)
                    {
                        sf::CircleShape projectile;
                        projectile.setFillColor(sf::Color::Red);
                        projectile.setPosition(pos_x, pos_y);
                        projectile.setRadius(5.0f);
                        projectiles.push_back(projectile);
                        projectiles_id.push_back(std::make_pair(id, projectile));
                    }
                }
                if (recv_buffer[0] == 0x07)
                {
                    _health = recv_buffer[1];
                    _score = recv_buffer[2];

                    std::cout << "Received player health: " << _health << " and score: " << _score
                              << std::endl;
                }
                if (recv_buffer[0] == 0x011)
                {
                    int id = recv_buffer[1];
                    window.clear();
                    for (int i = 0; i < players_id.size(); i++)
                    {
                        if (players_id[i].first == id)
                        {
                            players_id.erase(players_id.begin() + i);
                        }
                    }
                    game_over = true;
                }
            }

            if (game_over)
            {
                window_manager.drawText("Game Over", 10, 10, sf::Color::Red, window);
                window.display();
                std::this_thread::sleep_for(std::chrono::seconds(5));
                window.close();
            }
            else
            {
                float deltaTime = clock.restart().asSeconds();
                parallax.update(deltaTime);
                window.clear();
                parallax.draw(window);
                for (int i = 0; i < enemies_id.size(); i++)
                {
                    std::string color = get_enemy_color(enemies_id[i].first);
                    enemies_id[i].second.update(color);
                    enemies_id[i].second.render(window, color);
                }
                window_manager.drawText("Player Health: " + std::to_string(_health), 10, 10,
                                        sf::Color::Green, window);
                window_manager.drawText("Player Score: " + std::to_string(_score), 10, 40,
                                        sf::Color::Yellow, window);
                for (int i = 0; i < projectiles_id.size(); i++)
                {
                    window.draw(projectiles_id[i].second);
                }
                for (int i = 0; i < players_id.size(); i++)
                {
                    std::string color = get_player_color(players_id[i].first);
                    std::cout << "Player color: " << color << std::endl;
                    players_id[i].second.update(color);
                    players_id[i].second.render(window, color);
                }
                window.display();
            }
        }
    }
    catch (std::exception &e)
    {
        std::cerr << "UDP Exception: " << e.what() << "\n";
    }
}

Client::~Client()
{
}

// int main(int ac, char **av)
// {
//     Client client;
//     server_me_t server_me;
//     // if (recup_args(&server_me, ac, av) == false){
//     //     return (84);

//     // }
//     protocol::PlayerAction player_action = {1, 1, {0x04, 0x02}};
//     protocol::GameStateUpdate game_state_update = {{0x64, 0x04}};

//     std::string server_ip = "127.0.0.1";

//     std::cout << "Starting client..." << std::endl;
//     std::thread udp_thread(&Client::send_udp_message, &client, player_action, server_ip,
//     12346); std::thread tcp_thread(&Client::send_tcp_message, &client, player_action,
//     server_ip, 12345);

//     udp_thread.join();
//     tcp_thread.join();

//     return 0;
// }
```


