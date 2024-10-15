# Multiplayer Setup

The multiplayer setup in **R-Type** allows players to connect to a central server to coordinate gameplay, share state updates, and interact in real time. This section explains the architecture, protocols, and processes involved in setting up and managing multiplayer sessions.

---

## Architecture Overview

R-Type uses a **client-server architecture**:  
- **Server**: Manages game logic, player states, and synchronization.  
- **Clients**: Send player inputs to the server and render game events received from the server.

**Communication Protocols:**
- **UDP**: For fast, non-blocking communication (player movements, game state updates).

---

## Multiplayer Flow

The following ASCII diagram summarizes how players interact with the server and each other in multiplayer mode.

```ascii
+-------------------+           +-------------------+
|      Client 1     |           |      Client 2     |
| [Controls Player] |           | [Controls Player] |
+-------------------+           +-------------------+
           \                          /
            \                        /
             \                      /
           +---------------------------+
           |         Server            |
           |  - Syncs Game State       |
           |  - Handles Player Inputs  |
           |  - Manages Rooms          |
           +---------------------------+
                        |
           +----------------------------+
           |         Database           |
           |  - Stores Room Info        |
           |  - Tracks Player Scores    |
           +----------------------------+
```

---

## Player Lifecycle in Multiplayer

### 1. **Connecting to the Server**
1. Players initiate a connection by sending a **login request** over **UDP**.
2. The server responds with an acknowledgment, and the player is spawned in the game world.

**Protocol Command:**  
`0x01` → **Player Connected**  

### 2. **Joining or Creating a Room**

Players can either:
- **List Available Rooms**  
  Command: `LIST_ROOMS`  
- **Join a Room**  
  Command: `JOIN_ROOM <room_id>`  
- **Create a Room**  
  Command: `CREATE_ROOM <room_name>`  

If the player is idle for too long, the server will mark them as disconnected.  

### 3. **In-Game Communication and State Synchronization**
- **Movement and Input Updates**: Sent over **UDP** to avoid latency issues.  
- **Game Events** (such as enemy deaths or power-ups): Broadcasted by the server to all clients.

**Protocol:**  
`0x03` + Direction (`0x01` = Up, `0x02` = Down, etc.)  
The server calculates the new position and sends it to all clients.

### 4. **Player Disconnection Handling**
If a player disconnects (either by closing the game or crashing), the server notifies all connected clients.

```ascii
+-----------+                +--------------+
|   Player  |  ------->      |    Server    |
+-----------+   Disconnect   +--------------+
                Notifies other players:
   "Player 1 has disconnected."
```

---

## Room System and Matchmaking

The **Room System** allows players to form lobbies, create custom matches, or join existing rooms.

### Room Management Commands
1. **LIST_ROOMS**  
   - Lists all available rooms for players to join.
2. **JOIN_ROOM <room_id>**  
   - Joins the specified room.
3. **CREATE_ROOM <room_name>**  
   - Creates a new room with the given name.

---

## Multiplayer Setup Flow

```ascii
[Client 1]   --->   Connect to Server   --->   [Server]
                    Send: 0x01 Player Connected

[Client 2]   --->   Connect to Server   --->   [Server]

[Both Clients]   --->  Play the Game  --->  [Server]
```

---

## Player Input

Below is how player inputs are sent to the server for movement and shooting:

```ascii
[Client]   --->   0x03 + 0x01 (Move Up)    --->    [Server]
[Client]   --->   0x04 (Fire Missile)      --->    [Server]
```

The server sends back updated positions and game state to all clients over UDP.

---

## Handling Disconnections

The server monitors all clients using **heartbeat signals** to ensure they are still active. If no signal is received for a certain period, the server:
1. **Marks the client as disconnected**.
2. **Removes the client from the room**.
3. **Notifies other clients**.

```ascii
+-----------+                +--------------+
|  Player 1 |   Timeout -->  |    Server    |
+-----------+                +--------------+
 "Player 1 has disconnected." Broadcast to other players.
```

---

## Heartbeat Monitoring

This example ensures the server keeps track of client connections.

```cpp
void Server::start_heartbeat_monitor() {
    std::thread([this]() {
        while (true) {
            auto now = std::chrono::steady_clock::now();
            for (auto it = clients_me.begin(); it != clients_me.end();) {
                auto time_since_last_ping = 
                    std::chrono::duration_cast<std::chrono::seconds>(
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
