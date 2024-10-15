### Detailed Documentation for Multiplayer Game Server and Client

---

## 1. Overview

This project involves the development of a multiplayer game using the **Entity-Component-System (ECS)** pattern, facilitated by the **UDP protocol** for real-time communication between the server and clients. The server manages player states, enemy entities, game logic, and real-time synchronization with multiple clients. The client handles player input, rendering, and interaction with the game environment.

This documentation will describe the server and client functionality, focusing on the UDP-based communication protocol, ECS architecture, and how the server and client interact to ensure a responsive, real-time multiplayer experience.

---

## 2. Protocol Design (UDP)

Communication between the server and client is conducted using **UDP**, which is well-suited for fast-paced games due to its low-latency characteristics. However, because UDP does not guarantee message delivery, custom handling for dropped packets and acknowledgment (ACK) has been implemented.

### Message Structure:

Messages exchanged between the server and the client are byte-encoded and follow a structured format for different types of game actions and events. 

| **Code** | **Direction** | **Description**                                      |
|----------|----------------|------------------------------------------------------|
| `0x01`   | Client → Server | Player creation                                      |
| `0x02`   | Server → Client | Client connection acknowledged                       |
| `0x03`   | Client → Server | Player input (up, down, left, right)                 |
| `0x04`   | Server → Client | Update all player positions                          |
| `0x05`   | Server → Client | Update enemy positions                               |
| `0x07`   | Server → Client | Send player health and score                         |
| `0x08`   | Server → Client | Notify about destroyed entities (dead players, enemies, missiles) |
| `0x09`   | Server → Client | Spawn new enemies                                    |
| `0x10`   | Server → Client | Missile positions                                    |
| `0x11`   | Server → Client | Coin positions                                       |

This structure ensures clear communication and synchronization between the server and clients.

---

## 3. Server Architecture

### 3.1 Server Overview

The server is responsible for handling multiple clients, managing the game state, and ensuring that each player receives timely updates about the game environment. The game server employs an **ECS** pattern to efficiently manage entities like players, enemies, missiles, and coins. It also uses **Boost.Asio** for asynchronous networking to handle both TCP (initial connections) and UDP (real-time game updates).

### 3.2 Key Components

- **Registry**: Stores all entities in the game, including components like position, velocity, health, etc.
- **Systems**: Handles the game logic for movement, collision detection, shooting, and other mechanics.
- **UDP Communication**: Sends and receives game state updates, player inputs, and entity changes.
- **Heartbeat Monitoring**: Tracks client activity and handles disconnection if a client stops responding.

### 3.3 Server Functionality

- **Handling Client Connections**:
    - The server listens on a UDP socket for new connections. Once a connection request is received (`0x01` from the client), the server acknowledges the connection (`0x02`).
  
- **Game State Management**:
    - The server manages the state of the game world, including player positions, health, scores, and the position of entities (enemies, missiles, coins).
    - Player inputs (`0x03`) are received from the client, and based on these inputs, the server updates the player’s position and sends back the updated state of the world (`0x04` to `0x11`).

- **Real-Time Updates**:
    - The server processes updates in a game loop. It handles inputs, updates entity positions, detects collisions, and broadcasts changes back to all connected clients.

- **Room and Session Management**:
    - The server can manage different game rooms, allowing players to join, leave, or create rooms dynamically.

### 3.4 Important Classes

- **`Server`**: Manages the main game loop, handles UDP communication, processes messages, and updates the ECS registry.
    - Methods:
        - `process_message`: Handles incoming UDP messages from clients.
        - `start_udp_server`: Initializes the UDP server to listen for client messages.
        - `notify_clients_of_disconnection`: Sends a notification when a client disconnects.
        - `handle_room_creation`: Manages room creation by players.
        - `run_game`: Main loop that runs the game logic.

- **`MovementSystem`**, **`ShootSystem`**, **`CollisionSystem`**: Handle movement, shooting, and collision detection logic, respectively.

- **`TimeManager`**: Manages time-based events, such as enemy spawning or shooting intervals.

---

## 4. Client Architecture

### 4.1 Client Overview

The client is responsible for sending player inputs to the server and receiving game state updates from the server. It also manages the local game state for rendering and interacts with the ECS to update entities on the client side. The client uses **Boost.Asio** for UDP communication with the server.

### 4.2 Key Components

- **Input Handling**: Captures player input (up, down, left, right) and sends it to the server in real-time.
- **UDP Communication**: Receives updates from the server (positions of players, enemies, missiles) and sends inputs for player actions.
- **Game State Rendering**: Uses the ECS system to render the updated game state on the client screen.

### 4.3 Client Functionality

- **Player Creation**:
    - When a player joins, the client sends a `0x01` message to the server requesting player creation. The server acknowledges with `0x02`.
  
- **Input Handling**:
    - The client captures player input (movement, shooting, etc.) and sends it to the server using message `0x03`. The inputs are byte-encoded, allowing the server to process player actions quickly.

- **Receiving Game Updates**:
    - The client receives frequent updates from the server, including new positions of players (`0x04`), enemies (`0x05`), and other entities like coins and missiles (`0x09`, `0x10`). The client then updates its local ECS and re-renders the game world accordingly.

- **Error Handling and Acknowledgment**:
    - Since UDP does not guarantee message delivery, the client handles packet loss by re-sending critical information if acknowledgment isn't received in a timely manner.

### 4.4 Important Classes

- **`Client`**: Manages communication with the server, sends inputs, and updates the game state based on server responses.
    - Methods:
        - `send_player_input`: Sends player input (e.g., movement direction) to the server.
        - `receive_game_state`: Receives and processes game state updates from the server.
        - `process_server_message`: Decodes the server's message and updates the local ECS accordingly.

- **Entity-Component System (ECS)**: Manages entities on the client side, allowing for efficient updates and rendering based on server messages.

---

## 5. Communication Workflow

### Server-Client Interaction Flow

1. **Player Connection**: 
    - Client sends a connection request (`0x01`) to the server.
    - Server acknowledges the connection and sends back `0x02`.

2. **Player Input Handling**:
    - Client sends player inputs (`0x03`) to the server, indicating movement directions.
    - Server processes the input, updates the game state, and broadcasts the updated player and entity positions to all clients.

3. **Entity State Update**:
    - Server sends updates about player positions, enemy positions, and missile/coin positions to the clients using messages (`0x04` to `0x11`).

4. **Disconnection**:
    - If a client disconnects, the server notifies all other clients using a disconnection message, updating the game state accordingly.

---
