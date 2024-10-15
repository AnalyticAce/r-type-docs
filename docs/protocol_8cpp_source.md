

# File protocol.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**protocol.cpp**](protocol_8cpp.md)

[Go to the documentation of this file](protocol_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** protocol
** File description:
** protocol
*/

#include "../../include/Server/protocol.hpp"

namespace protocol
{

    std::vector<uint8_t> serialize(const PlayerAction &msg)
    {
        std::vector<uint8_t> buffer;
        buffer.push_back(static_cast<uint8_t>(MessageType::PLAYER_ACTION));
        buffer.insert(buffer.end(), reinterpret_cast<const uint8_t *>(&msg.player_id),
                      reinterpret_cast<const uint8_t *>(&msg.player_id) + sizeof(msg.player_id));
        buffer.push_back(msg.action_type);
        buffer.insert(buffer.end(), msg.data.begin(), msg.data.end());
        return buffer;
    }

    std::vector<uint8_t> serialize(const GameStateUpdate &msg)
    {
        std::vector<uint8_t> buffer;
        buffer.push_back(static_cast<uint8_t>(MessageType::GAME_STATE_UPDATE));
        buffer.insert(buffer.end(), msg.state_data.begin(), msg.state_data.end());
        return buffer;
    }

    std::vector<uint8_t> serialize(const EventNotification &msg)
    {
        std::vector<uint8_t> buffer;
        buffer.push_back(static_cast<uint8_t>(MessageType::EVENT_NOTIFICATION));
        buffer.push_back(msg.event_type);
        buffer.insert(buffer.end(), msg.event_data.begin(), msg.event_data.end());
        return buffer;
    }

    bool deserialize(const std::vector<uint8_t> &buffer, PlayerAction &msg)
    {
        if (buffer.empty() || buffer[0] != static_cast<uint8_t>(MessageType::PLAYER_ACTION))
            return false;

        size_t offset = 1;
        msg.player_id = *reinterpret_cast<const uint32_t *>(&buffer[offset]);
        offset += sizeof(msg.player_id);
        msg.action_type = buffer[offset++];
        msg.data.assign(buffer.begin() + offset, buffer.end());
        return true;
    }

    bool deserialize(const std::vector<uint8_t> &buffer, GameStateUpdate &msg)
    {
        if (buffer.empty() || buffer[0] != static_cast<uint8_t>(MessageType::GAME_STATE_UPDATE))
            return false;

        msg.state_data.assign(buffer.begin() + 1, buffer.end());
        return true;
    }

    bool deserialize(const std::vector<uint8_t> &buffer, EventNotification &msg)
    {
        if (buffer.empty() || buffer[0] != static_cast<uint8_t>(MessageType::EVENT_NOTIFICATION))
            return false;

        size_t offset = 1;
        msg.event_type = buffer[offset++];
        msg.event_data.assign(buffer.begin() + offset, buffer.end());
        return true;
    }
} // namespace protocol
```


