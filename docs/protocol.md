# R-TYPE Multiplayer Game Protocol (MGP) over UDP

The Multiplayer Game Protocol (MGP) is a communication protocol designed for real-time multiplayer games, specifically for the R-TYPE game. This document outlines the structure and functionality of MGP, which operates over UDP to facilitate efficient and low-latency communication between a server and multiple clients.

## 2. Terminology

- **Client**: The player-side application.
- **Server**: The authoritative source for player and entity positions, game state, etc.
- **Entity**: A game object (players, enemies, etc.).
- **ID**: A unique identifier for each entity.

## 3. Protocol Overview

MGP operates over UDP to prioritize real-time performance. The protocol consists of simple hexadecimal identifiers (opcodes) followed by data payloads. Both the server and the client exchange these messages to synchronize game states.

## 4. Message Structure

Each message consists of:

- **Opcode**: A 1-byte hexadecimal identifier indicating the type of message.
- **Payload**: Additional data (e.g., position, player life) relevant to the message.

```
+---------------------+
|      Message        |
+---------------------+
| Opcode (1 Byte)     |
+---------------------+
| Payload (Variable)  |
+---------------------+
```

## 5. Message Types

### 5.1. Client to Server Messages

#### 5.1.1. 0x01: Client Connection Request

- **Description**: The client sends this message to request a connection to the server.
- **Payload**: None.
- **Server Response**: The server responds with `0x02` (Connection Acknowledgment).

#### 5.1.2. 0x03: Client Input (Movement)

- **Description**: The client sends movement inputs to the server.
- **Payload**:

  | Field       | Size (bytes) | Description                             |
  |-------------|--------------|-----------------------------------------|
  | Input   | 1            | Direction of movement.                  |

  - Possible values for Input:
    - 0x01: Up
    - 0x02: Down
    - 0x03: Left
    - 0x04: Right

- **Server Response**: The server processes the input and updates player positions.

#### 5.1.3. Additional Client Messages

- **Description**: Clients can send other messages based on game design (e.g., shooting, item pickup). These are assigned specific opcodes based on game requirements.

### 5.2. Server to Client Messages

#### 5.2.1. 0x02: Server Acknowledgment of Connection

- **Description**: The server sends this message to acknowledge a client's connection request.
- **Payload**: None.

#### 5.2.2. 0x05: Player Position Update

- **Description**: The server broadcasts updated player positions to all clients.
- **Payload**:

  | Field       | Size (bytes) | Description                             |
  |-------------|--------------|-----------------------------------------|
  | PlayerID| 1            | ID of the player being updated.         |
  | X Pos   | 2            | X coordinate of the player.             |
  | Y Pos   | 2            | Y coordinate of the player.             |

  This message contains the positions of all players currently connected to the game.

#### 5.2.3. 0x07: Player Life and Score Update

- **Description**: The server sends updates on a player's life and score.
- **Payload**:

  | Field       | Size (bytes) | Description                             |
  |-------------|--------------|-----------------------------------------|
  | PlayerID| 1            | ID of the player whose data is updated. |
  | Life    | 1            | Remaining life of the player.           |
  | Score   | 2            | Player’s current score.                 |

#### 5.2.4. 0x09: Entity Death Notification

- **Description**: The server notifies clients of entities (e.g., enemies) that have been destroyed.
- **Payload**:

  | Field       | Size (bytes) | Description                             |
  |-------------|--------------|-----------------------------------------|
  | EntityID| 1            | ID of the entity that was destroyed.    |

#### 5.2.5. 0x04: Player Disconnection Notice

- **Description**: The server sends this message when a player disconnects from the game.
- **Payload**:

  | Field       | Size (bytes) | Description                             |
  |-------------|--------------|-----------------------------------------|
  | PlayerID| 1            | ID of the player who disconnected.      |

#### 5.2.6. Other Server Messages

- **Description**: Additional messages can be implemented based on specific game requirements, such as broadcasting new enemies, missiles, or item pickups (e.g., coins).

## 6. Message Flow

1. **Client Connection**
   - The client sends `0x01` (Connection Request).
   - The server responds with `0x02` (Connection Acknowledgment).

2. **Client Movement Input**
   - The client sends `0x03` with a movement direction.
   - The server processes the movement and sends updated positions using `0x05` to all clients.

3. **Player Status Updates**
   - The server periodically sends `0x07` to update each client’s life and score.
   - If any entities die during the game, the server broadcasts `0x09` to notify all clients.

4. **Disconnection Handling**
   - If a player disconnects, the server sends `0x04` to all clients to notify them of the disconnection.

## 7. Error Handling

UDP is a connectionless protocol, and there is no guarantee of message delivery. Therefore, the protocol should handle the following cases:

- **Lost Packets**: If a message is not received, the client should resend input, and the server should regularly broadcast state updates.
- **Out-of-Order Packets**: The client must be prepared to handle messages arriving in the wrong order (e.g., receiving player status before the initial connection acknowledgment).

## 8. Security Considerations

Since this protocol runs over UDP, it is vulnerable to spoofing and man-in-the-middle attacks. Therefore, implementing encryption or adding a verification layer at the application level is recommended.

## 9. Conclusion

The MGP protocol is designed for efficient real-time communication between a server and multiple clients in a multiplayer game. It leverages the low-latency benefits of UDP while ensuring synchronization of player actions and game states.