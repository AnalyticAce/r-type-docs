# Gameplay Overview

## Game Objective

R-Type is a horizontal scrolling **shoot-'em-up** game where players pilot a spaceship to fight waves of enemies called the **Bydos**. The goal is to survive through levels filled with enemies, obstacles, and bosses, using strategic movement and shooting skills.

---

## Players and Controls

Each player controls a spaceship using the following inputs:

- **Arrow Keys**: 
    - Up, Down, Left, and Right to move.
- **Fire Button**: Shoot missiles.
- **Special Attack**: Launch charged shots (if available).

**Gameplay Actions:**  
1. Player connection is initiated with the command:
   **`0x01`** - Spawns the player in the game.  
2. Movement commands:
   **`0x03` + Direction Codes**  
   Example:
   - `0x03 0x01` → Move Up  
   - `0x03 0x02` → Move Down  
   - `0x03 0x03` → Move Left  
   - `0x03 0x04` → Move Right  

---

## Game World

The game screen scrolls horizontally at a constant pace, with various elements dynamically appearing.

```ascii
+-------------------------------------------------------------------+
|                     Starfield Scrolling Background                |
|                                                                   |
|         Player 1 --> [P1]                 Monster --> [M]         |
|                      +--------+            +-----+                |
|         Player 2 --> [P2]      Missile --> [ ]--->                |
|                       *Power-up Spawner                           |
|                                                                   |
|         Obstacles --> [X]   Boss --> [B]                          |
+-------------------------------------------------------------------+
```

### Key Gameplay Elements:
1. **Starfield Background**: A scrolling starry space environment.
2. **Players (P1, P2, etc.)**: Up to 4 players with distinct sprites.
3. **Bydos Enemies (M)**: Various monsters with unique patterns and attacks.
4. **Obstacles (X)**: Static or moving barriers blocking players.
5. **Bosses (B)**: Powerful enemies with multiple attack phases.
6. **Power-ups**: Items spawning randomly to upgrade players' abilities.

---

## Gameplay Flow

1. **Player Spawning**  
   Upon connecting (`0x01`), the player spaceship appears on the left side of the screen.

2. **Movement and Input Handling**  
   The player sends movement commands (e.g., `0x03` for movement + direction code) to the server. The server synchronizes the game state across all connected clients.

3. **Enemy Spawn and Interaction**  
   Enemies randomly appear on the right side and move left. Players must shoot them down using missiles and special attacks.

4. **Power-ups and Obstacles**  
   Destroying certain enemies spawns power-ups. Players collect these for enhancements. Obstacles add complexity to movement.

5. **Boss Battles**  
   At the end of each level, players encounter a boss. Players must coordinate to defeat it while avoiding attacks.

---

## Networking and Synchronization

The game follows a **client-server architecture**, where the server manages game logic and synchronizes it with the clients. All in-game communication, such as movement and enemy positions, uses **UDP packets** to ensure low-latency communication.

### Player Command Protocol:
- **`0x01`**: Player connection and spawning.
- **`0x03` + Movement**: Moves the player in the specified direction.
- **`0x04` + Fire**: Fires a missile.
- **`0x05` + Special Attack**: Triggers a charged shot.

The server ensures consistency by notifying all clients about:
- Player movements.
- Enemy spawns and deaths.
- Power-up availability.
- Boss encounters.

---

## ASCII Representation of a Game Round

```ascii
+---------------------------------------------------------------+
| [P1]          *       [M]       [M]         [B]               |
|               |                 |                             |
|        [P2]--->                 +-------> [ ]--->             |
|                           Power-up Spawner                    |
|  [X]            [P3]   +--------------------+                 |
|                                                               |
|                       BOSS Fight!                             |
+---------------------------------------------------------------+
```

In this scenario:
- P1 and P2 are actively shooting enemies.
- A boss (B) is advancing, with players coordinating to defeat it.
- Power-ups are available for collection.