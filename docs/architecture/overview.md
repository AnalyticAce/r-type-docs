# Architecture Overview

The **R-Type multiplayer architecture** is designed to allow players to connect and interact in real-time with a server using **UDP-based communication**. The server handles all game logic, player synchronization, and disconnections while ensuring smooth gameplay. 

This architecture emphasizes **low-latency UDP** communication for faster updates and **reliable disconnection handling**, using a **heartbeat mechanism** to detect and notify other players of dropped connections.

---

## System Architecture

```ascii
+--------------------+               +----------------------+
|      Client 1      |               |      Client 2        |
| [Sends Player Input]               | [Sends Player Input] |
+--------------------+               +----------------------+
            \                            /
             \                          /
              \                        /
            +------------------------------+
            |         R-Type Server        |
            |  - Processes Player Inputs   |
            |  - Syncs Game State          |
            |  - Manages Rooms & Players   |
            |  - Handles Disconnections    |
            +------------------------------+
```

### Key Components
1. **Server:**  
    - Central authority managing the game state and synchronizing clients.
    - Processes player input, updates game states, and manages rooms.
    - Uses **UDP communication** to ensure low-latency updates.  

2. **Clients:**  
    - Send player actions and input updates to the server.
    - Render the game state based on server updates.
    - Monitor and maintain connection with the server via **heartbeat pings**.

---

## Communication Flow

Since the architecture relies **solely on UDP**, all communication (including player input, game state updates, and room management) is done using **UDP datagrams**.

---

### UDP Communication Flow

```ascii
[Client 1] ---> (Move Up) ---> [Server]
                          ---> Updates Position
                          ---> Broadcasts New State to All Clients
[Client 2] <--- (Position Update) <--- [Server]
```

1. **Player Input:**  
   - Clients send input actions (e.g., movement, shooting) to the server using UDP.  
   - Example:  
     **Protocol Command:**  
     `0x03` + `Direction` (0x01 = Up, 0x02 = Down, etc.).

2. **Game State Updates:**  
   - The server processes input and sends back the updated player positions and game state to all connected clients.

---

## Player Lifecycle Overview

### 1. **Connecting to the Server**
- Each client initiates a connection by sending a **UDP "connect" message**.  
- The server responds with an acknowledgment and assigns the client to a room or the game world.

---

### 2. **Heartbeat Monitoring & Disconnection Handling**

To ensure the server remains operational even if a client disconnects unexpectedly, the server implements a **heartbeat mechanism**.

```ascii
+------------+          +--------------+
|  Client 1  |  ----->  |   Server     |
+------------+   Ping   +--------------+
           If no ping received in 10s:
            [Server]: "Client 1 Disconnected"
```

**Code Snippet: Heartbeat Monitoring**

```cpp
void Server::start_heartbeat_monitor(boost::asio::io_context &io_context) {
    std::thread([this]() {
        while (true) {
            auto now = std::chrono::steady_clock::now();
            for (auto it = clients_me.begin(); it != clients_me.end();) {
                auto time_since_last_ping = std::chrono::duration_cast<std::chrono::seconds>(
                    now - it->second.last_ping);

                if (time_since_last_ping.count() > 10) {
                    notify_clients_of_disconnection(io_context, it->first);
                    it = clients_me.erase(it);
                } else {
                    ++it;
                }
            }
            std::this_thread::sleep_for(std::chrono::seconds(1));
        }
    }).detach();
}
```

- **Disconnection Detection:**  
  If a client’s ping is not received within 10 seconds, the server marks the client as disconnected and notifies other players.

---

## Room System for Matchmaking

The **Room System** allows players to create, join, or leave rooms. Each room maintains its own player list, and the server tracks player movements and game state updates within each room.

### Room Management Commands

```ascii
[Client] ---> CREATE_ROOM "Room1" ---> [Server]
[Client] ---> JOIN_ROOM "Room1" ---> [Server]
[Client] ---> LIST_ROOMS ---> [Server]
```

1. **Create a Room:**  
    - Players can create rooms to host matches.
    - Example Command: `CREATE_ROOM <room_name>`  
    - The server creates the room and waits for other players to join.

2. **Join a Room:**  
    - Players can join existing rooms by sending the **room ID**.
    - Example Command: `JOIN_ROOM <room_id>`  

3. **List Rooms:**  
    - Players can query available rooms.
    - Example Command: `LIST_ROOMS`

---

## Example Gameplay Sequence

1. **Client 1** sends `0x01` to connect to the server and gets assigned to a room.
2. **Client 2** joins the same room by sending `JOIN_ROOM Room1`.
3. Both clients start sending player inputs (`0x03 + Direction`).
4. The server updates player positions and broadcasts them back to all clients.
5. **Client 1** disconnects unexpectedly; the server detects it and notifies **Client 2**.

---
