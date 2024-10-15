

# File check\_message.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**check\_message.cpp**](check__message_8cpp.md)

[Go to the documentation of this file](check__message_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-rtype-kafui.hounkpatin
** File description:
** check_message
*/

#include "../../include/Server/Server.hpp"

int Server::get_player_id(const udp::endpoint &client_endpoint)
{
    int i = 1;
    for (auto client : _connected_clients)
    {
        if (client == client_endpoint)
        {
            return i;
        }
        i++;
    }
    return -1;
}

std::string Server::get_player_name(const udp::endpoint &client_endpoint)
{
    for (auto player : id_name)
    {
        if (player.first == client_endpoint)
        {
            return player.second;
        }
    }
    return "";
}

void Server::check_player_message(udp::socket &socket, const std::vector<uint8_t> &buffer,
                                  const udp::endpoint &client_endpoint)
{
    if (buffer.empty())
    {
        return;
    }
    std::string pl_name;
    uint8_t command = buffer[0];
    switch (command)
    {
    case 0x01:
    {
        std::cout << "Player connected from " << client_endpoint << std::endl;
        std::string response = "Player connected";
        socket.send_to(boost::asio::buffer(response), client_endpoint);
        break;
    }
    case 0x02:
    {
        if (buffer.size() < 21)
        {
            std::cerr << "Invalid player name input" << std::endl;
            return;
        }
        std::string player_name(buffer.begin() + 1, buffer.end());
        std::cout << "Player name: " << player_name << " from " << client_endpoint << std::endl;
        uint8_t command = 0x02;
        players_count++;
        std::vector<u_int16_t> response = {0x02, players_count};
        id_name.push_back(std::make_pair(client_endpoint, player_name));
        registry.spawn_player(player_name);
        registry.entity_update();
        game_run = true;
        int i = 1;
        for (auto client : _connected_clients)
        {
            socket.send_to(boost::asio::buffer(response), client);
        }
        std::vector<std::vector<u_int16_t>> updates;
        if (registry.get_entities("Player").size() > 0)
        {
            for (auto player : id_name)
            {
                auto pos = movement.move_player(registry, player.second);
                std::vector<u_int16_t> update = {0x05, static_cast<u_int16_t>(i),
                                                 static_cast<u_int16_t>(pos.x),
                                                 static_cast<u_int16_t>(pos.y)};
                std::cout << "New player position: (" << " id :" << i << " " << pos.x << ", "
                          << pos.y << ")" << std::endl;
                updates.push_back(update);
                i++;
            }
        }
        for (auto update : updates)
        {
            for (auto client : _connected_clients)
            {
                socket.send_to(boost::asio::buffer(update), client);
            }
        }
        u_int16_t health = 100;
        u_int16_t score = 0;
        std::vector<u_int16_t> player_info = {0x07, health, score};
        socket.send_to(boost::asio::buffer(player_info), client_endpoint);
        break;
    }
    case 0x03:
    {
        if (buffer.size() < 2)
        {
            std::cerr << "Invalid player movement input" << std::endl;
            return;
        }
        uint8_t direction = buffer[1];
        std::string move_direction;
        switch (direction)
        {
        case 0x01:
            move_direction = "keyup";
            break;
        case 0x02:
            move_direction = "keydown";
            break;
        case 0x03:
            move_direction = "keyleft";
            break;
        case 0x04:
            move_direction = "keyright";
            break;
        default:
            std::cerr << "Unknown direction" << std::endl;
            return;
        }

        auto it = std::find_if(id_name.begin(), id_name.end(),
                               [&client_endpoint](const std::pair<udp::endpoint, std::string> &pair)
                               { return pair.first == client_endpoint; });
        if (it != id_name.end())
        {
            pl_name = it->second;
        }
        else
        {
            std::cerr << "Player name not found for endpoint " << client_endpoint << std::endl;
            return;
        }
        Vector2D pos = {0, 0};
        movement.handleInput(registry, move_direction, pl_name);
        pos = movement.move_player(registry, pl_name);
        int id = get_player_id(client_endpoint);
        std::vector<u_int16_t> response = {0x03, static_cast<u_int16_t>(id),
                                           static_cast<u_int16_t>(pos.x),
                                           static_cast<u_int16_t>(pos.y)};
        std::vector<u_int16_t> update = {0x05, static_cast<u_int16_t>(id),
                                         static_cast<u_int16_t>(pos.x),
                                         static_cast<u_int16_t>(pos.y)};
        socket.send_to(boost::asio::buffer(response), client_endpoint);
        for (auto client : _connected_clients)
        {
            socket.send_to(boost::asio::buffer(update), client);
        }
        break;
    }
    case 0x06:
    {
    }
    default:
        std::cerr << "Unknown command received" << std::endl;
        break;
    }
}

void Server::check_player_position(udp::socket &socket, const std::vector<uint8_t> &buffer,
                                   const udp::endpoint &client_endpoint)
{
    if (buffer.empty())
    {
        return;
    }
    if (buffer.size() < 3)
    {
        std::cerr << "Invalid player position input" << std::endl;
        return;
    }
    uint8_t id = buffer[1];
    uint8_t pos_x = buffer[2];
    uint8_t pos_y = buffer[3];
    std::cout << "Player " << static_cast<int>(id) << " position: (" << static_cast<int>(pos_x)
              << ", " << static_cast<int>(pos_y) << ")" << std::endl;
    std::vector<u_int16_t> response = {0x05, id, pos_x, pos_y};
    for (auto client : _connected_clients)
    {
        socket.send_to(boost::asio::buffer(response), client);
    }
}
```


