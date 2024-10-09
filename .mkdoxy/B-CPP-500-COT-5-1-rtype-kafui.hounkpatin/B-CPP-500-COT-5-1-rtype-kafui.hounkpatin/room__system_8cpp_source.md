

# File room\_system.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**room\_system.cpp**](room__system_8cpp.md)

[Go to the documentation of this file](room__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-rtype-kafui.hounkpatin
** File description:
** room_system
*/

#include "../include/room_system.hpp"

Room_System::Room_System() : next_room_id(1) {}

Room_System::~Room_System() {}

int Room_System::create_room(const std::string &room_name, int max_players) {
  int room_id = next_room_id++;
  rooms[room_id] = {room_name, max_players, {}, false};
  std::cout << "Room created: " << room_name << " with ID " << room_id
            << std::endl;
  return room_id;
}

bool Room_System::join_room(int room_id, const std::string &player_name) {
  if (rooms.find(room_id) != rooms.end() && !rooms[room_id].in_game) {
    Room &room = rooms[room_id];
    if (room.players.size() < room.max_players) {
      room.players.push_back(player_name);
      std::cout << player_name << " joined room " << room.name << std::endl;

      if (room.players.size() == room.max_players) {
        start_game_in_room(room_id);
      }
      return true;
    }
  }
  return false;
}

void Room_System::leave_room(int room_id, const std::string &player_name) {
  if (rooms.find(room_id) != rooms.end()) {
    Room &room = rooms[room_id];
    auto it = std::find(room.players.begin(), room.players.end(), player_name);
    if (it != room.players.end()) {
      room.players.erase(it);
      std::cout << player_name << " left room " << room.name << std::endl;

      if (room.players.empty()) {
        remove_room(room_id);
      }
    }
  }
}

std::vector<std::string> Room_System::list_available_rooms() const {
  std::vector<std::string> available_rooms;
  for (const auto &pair : rooms) {
    const Room &room = pair.second;
    if (!room.in_game) {
      available_rooms.push_back(room.name +
                                " (ID: " + std::to_string(pair.first) + ")");
    }
  }
  return available_rooms;
}

void Room_System::start_game_in_room(int room_id) {
  if (rooms.find(room_id) != rooms.end()) {
    rooms[room_id].in_game = true;
    std::cout << "Game started in room: " << rooms[room_id].name << std::endl;
  }
}

void Room_System::remove_room(int room_id) {
  if (rooms.find(room_id) != rooms.end()) {
    std::cout << "Removing room: " << rooms[room_id].name << std::endl;
    rooms.erase(room_id);
  }
}

// int main() {
//     Room_System room_system;

//     int room1 = room_system.create_room("Alpha Room", 4);
//     int room2 = room_system.create_room("Beta Room", 3);

//     auto rooms = room_system.list_available_rooms();
//     for (const auto& room : rooms) {
//         std::cout << "Available room: " << room << std::endl;
//     }

//     room_system.join_room(room1, "Player1");
//     room_system.join_room(room1, "Player2");
//     room_system.join_room(room2, "Player3");

//     room_system.leave_room(room1, "Player1");

//     rooms = room_system.list_available_rooms();
//     for (const auto& room : rooms) {
//         std::cout << "Available room: " << room << std::endl;
//     }

//     return 0;
// }
```


