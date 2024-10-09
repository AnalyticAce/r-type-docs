

# File Client.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**Client.cpp**](Client_8cpp.md)

[Go to the documentation of this file](Client_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** client
** File description:
** Client
*/

#include "../include/Client.hpp"

using boost::asio::ip::tcp;
using boost::asio::ip::udp;

Client::Client() {}

void Client::send_tcp_message(const protocol::PlayerAction &message,
                              const std::string &server_ip, int server_port)
{
  try
  {
    boost::asio::io_context io_context;
    tcp::resolver resolver(io_context);
    tcp::resolver::query query(tcp::v4(), server_ip,
                               std::to_string(server_port));
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
  if (!font.loadFromFile("src/Server/src/04B_19__.TTF"))
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
  player.setFillColor(sf::Color::Green);
  player.setPosition(100, 100);
  players.push_back(player);
  players_id.push_back(std::make_pair(1, player));
}

void Client::create_player_2()
{
  sf::RectangleShape player(sf::Vector2f(50, 50));
  player.setFillColor(sf::Color::Yellow);
  player.setPosition(100, 300);
  players.push_back(player);
  players_id.push_back(std::make_pair(2, player));
}

void Client::create_player_3()
{
  sf::RectangleShape player(sf::Vector2f(50, 50));
  player.setFillColor(sf::Color::Blue);
  player.setPosition(600, 600);
  players.push_back(player);
  players_id.push_back(std::make_pair(3, player));
}

void Client::create_player_4()
{
  sf::RectangleShape player(sf::Vector2f(50, 50));
  player.setFillColor(sf::Color::Red);
  player.setPosition(600, 100);
  players.push_back(player);
  players_id.push_back(std::make_pair(4, player));
}


void Client::send_udp_message(const protocol::PlayerAction &message,
                              const std::string &server_ip, int server_port)
{
  try
  {
    boost::asio::io_context io_context;
    udp::resolver resolver(io_context);
    udp::resolver::query query(udp::v4(), server_ip,
                               std::to_string(server_port));
    udp::endpoint receiver_endpoint = *resolver.resolve(query).begin();

    udp::socket socket(io_context);
    socket.open(udp::v4());
    socket.non_blocking(true);
    uint8_t connect_message = 0x01;
    socket.send_to(boost::asio::buffer(&connect_message, 1), receiver_endpoint);
    std::cout << "Sent player connection request" << std::endl;

    std::string player_name = get_name();
    uint8_t name_message[21] = {0x02};
    for (int i = 0; i < player_name.size(); i++)
    {
      name_message[i + 1] = player_name[i];
    }
    socket.send_to(boost::asio::buffer(name_message, 21), receiver_endpoint);
    std::cout << "Sent player name: " << player_name << std::endl;

    window.create(sf::VideoMode(800, 600), "SFML window");

    int nb_players = 0;
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
            socket.send_to(boost::asio::buffer(move_message, 2), receiver_endpoint);
            std::cout << "Sent player movement: keyup" << std::endl;
          }
          if (sf::Keyboard::isKeyPressed(sf::Keyboard::Down))
          {
            uint8_t move_message[2] = {0x03, 0x02};
            socket.send_to(boost::asio::buffer(move_message, 2), receiver_endpoint);
            std::cout << "Sent player movement: keydown" << std::endl;
          }
          if (sf::Keyboard::isKeyPressed(sf::Keyboard::Left))
          {
            uint8_t move_message[2] = {0x03, 0x03};
            socket.send_to(boost::asio::buffer(move_message, 2), receiver_endpoint);
            std::cout << "Sent player movement: keyleft" << std::endl;
          }
          if (sf::Keyboard::isKeyPressed(sf::Keyboard::Right))
          {
            uint8_t move_message[2] = {0x03, 0x04};
            socket.send_to(boost::asio::buffer(move_message, 2), receiver_endpoint);
            std::cout << "Sent player movement: keyright" << std::endl;
          }
        }
      }
      window.clear();
      std::array<u_int16_t, 128> recv_buffer;
      udp::endpoint sender_endpoint;
      boost::system::error_code error;
      size_t len = socket.receive_from(boost::asio::buffer(recv_buffer), sender_endpoint, 0, error);

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
          std::cout << "Received UDP acknowledgment data: " << recv_buffer.data() << std::endl;
          int id = recv_buffer[1];
          float pos_x = static_cast<float>(recv_buffer[2]);
          float pos_y = static_cast<float>(recv_buffer[3]);

          for (auto &player : players_id) {
            if (player.first == id) {
              player.second.setPosition(pos_x, pos_y);
              std::cout << "Updated player " << id << " position to: (" << pos_x << ", " << pos_y << ")" << std::endl;
            }
          }
        }
        if (recv_buffer[0] == 0x02)
        {
          nb_players = recv_buffer[1];
          std::cout << "Received UDP acknowledgment data: " << recv_buffer.data() << std::endl;
          std::cout << "Players size : " << nb_players << std::endl;
          if (nb_players >= 1 && players_id.size() == 0){
            create_player_1();
          }
          if (nb_players >= 2 && players_id.size() == 1){
            create_player_2();
          }
          if (nb_players >= 3 && players_id.size() == 2){
            create_player_3();
          }
          if (nb_players >= 4 && players_id.size() == 3){
            create_player_4();
          }
          std::cout << "Received updated game state" << std::endl;
        }
        if (recv_buffer[0] == 0x04)
        {
          int v = 0;
          int id = recv_buffer[1];
          int pos_x = recv_buffer[2];
          int pos_y = recv_buffer[3];
          for (auto &enemy : enemies_id) {
            if (enemy.first == id) {
              enemy.second.setPosition(pos_x, pos_y);
              std::cout << "Updated enemy " << id << " position to: (" << pos_x << ", " << pos_y << ")" << std::endl;
              v = 1;
            }
          } if (v == 0) {
            sf::CircleShape enemy;
            enemy.setFillColor(sf::Color::Yellow);
            enemy.setPosition(pos_x, pos_y);
            enemy.setRadius(10.0f);
            enemies.push_back(enemy);
            enemies_id.push_back(std::make_pair(id, enemy));
          }
        }
        if (recv_buffer[0] == 0x05)
        {
          int id = recv_buffer[1];
          float pos_x = static_cast<float>(recv_buffer[2]);
          float pos_y = static_cast<float>(recv_buffer[3]);
          std::cout << "Received player id :" <<  id << "position: (" << pos_x << ", " << pos_y << ")" << std::endl;
          for (auto &player : players_id) {
            if (player.first == id) {
              player.second.setPosition(pos_x, pos_y);
            }
          }
        }
      }
      for (int i = 0 ; i < nb_players; i++)
      {
        window.draw(players_id[i].second);
      }
      for (int i = 0 ; i < enemies_id.size(); i++)
      {
        window.draw(enemies_id[i].second);
      }
      window.display();
    }
  }
  catch (std::exception &e)
  {
    std::cerr << "UDP Exception: " << e.what() << "\n";
  }
}

Client::~Client() {}

int main(int ac, char **av)
{
  Client client;
  server_me_t server_me;
  // if (recup_args(&server_me, ac, av) == false){
  //     return (84);

  // }
  protocol::PlayerAction player_action = {1, 1, {0x04, 0x02}};
  protocol::GameStateUpdate game_state_update = {{0x64, 0x04}};

  std::string server_ip = "192.168.244.218";

  std::cout << "Starting client..." << std::endl;
  std::thread udp_thread(&Client::send_udp_message, &client, player_action,
                         server_ip, 12346);
  std::thread tcp_thread(&Client::send_tcp_message, &client, player_action,
                         server_ip, 12345);

  udp_thread.join();
  tcp_thread.join();

  return 0;
}
```


