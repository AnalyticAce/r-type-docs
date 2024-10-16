

# File server\_room.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**server\_room.cpp**](server__room_8cpp.md)

[Go to the documentation of this file](server__room_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-rtype-kafui.hounkpatin
** File description:
** server_room
*/

#include "../../include/Server/Server.hpp"

void Server::process_message_contain(udp::socket &socket, const std::vector<uint8_t> &buffer,
                                     const udp::endpoint &client_endpoint)
{
    std::string command(buffer.begin(), buffer.end());
    std::cout << command << std::endl;
    if (command.starts_with("CREATE_ROOM"))
    {
        std::cout << "received 1" << std::endl;
        std::string room_name = command.substr(12);
        handle_room_creation(socket, room_name, client_endpoint);
    }
    else if (command.starts_with("JOIN_ROOM"))
    {
        std::cout << "received 2" << std::endl;
        int room_id = std::stoi(command.substr(10));
        handle_room_joining(socket, room_id, client_endpoint);
    }
    else if (command == "LIST_ROOMS")
    {
        std::cout << "received 3" << std::endl;
        handle_list_rooms(socket, client_endpoint);
    }
}

void Server::handle_room_creation(udp::socket &socket, const std::string &room_name,
                                  const udp::endpoint &client_endpoint)
{
    int room_id = room_system.create_room(room_name, 4);
    clients[client_endpoint] = room_name;

    std::string response = "Room created: " + room_name + " (ID: " + std::to_string(room_id) + ")";
    std::cout << response << std::endl;
    socket.send_to(boost::asio::buffer(response), client_endpoint);
}

void Server::handle_room_joining(udp::socket &socket, int room_id,
                                 const udp::endpoint &client_endpoint)
{
    std::string player_name = client_endpoint.address().to_string();

    bool joined = room_system.join_room(room_id, player_name);
    std::string response =
        joined ? "Joined room " + std::to_string(room_id) : "Failed to join room";
    std::cout << response << std::endl;
    socket.send_to(boost::asio::buffer(response), client_endpoint);
}

void Server::handle_list_rooms(udp::socket &socket, const udp::endpoint &client_endpoint)
{
    std::vector<std::string> rooms = room_system.list_available_rooms();
    std::string response = "Available rooms:\n";

    for (const std::string &room : rooms)
    {
        response += room + "\n";
    }
    std::cout << response << std::endl;
    socket.send_to(boost::asio::buffer(response), client_endpoint);
}
```


