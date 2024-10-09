

# File protocol.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**protocol.hpp**](protocol_8hpp.md)

[Go to the documentation of this file](protocol_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** protocol
** File description:
** protocol
*/

#ifndef PROTOCOL_HPP_
#define PROTOCOL_HPP_
#include <cstddef>
#include <cstdint>
#include <iostream>
#include <vector>

namespace protocol {

enum class MessageType : uint8_t {
  PLAYER_ACTION = 1,
  GAME_STATE_UPDATE = 2,
  EVENT_NOTIFICATION = 3
};

struct PlayerAction {
  uint32_t player_id;
  uint8_t action_type;
  std::vector<uint8_t> data;
};

struct GameStateUpdate {
  std::vector<uint8_t> state_data;
};

struct EventNotification {
  uint8_t event_type;
  std::vector<uint8_t> event_data;
};

std::vector<uint8_t> serialize(const PlayerAction &msg);
std::vector<uint8_t> serialize(const GameStateUpdate &msg);
std::vector<uint8_t> serialize(const EventNotification &msg);

bool deserialize(const std::vector<uint8_t> &buffer, PlayerAction &msg);
bool deserialize(const std::vector<uint8_t> &buffer, GameStateUpdate &msg);
bool deserialize(const std::vector<uint8_t> &buffer, EventNotification &msg);
} // namespace protocol

#endif /* !PROTOCOL_HPP_ */
```


