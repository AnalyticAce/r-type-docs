# Controls
## Game Instructions: How to Play the Multiplayer Game

Welcome to the **multiplayer UDP-based game**! This guide will help you understand how to play, control your character, and interact with other players in the game world.

---

### **1. Getting Started**

- **Client Connection**: As a player, you will be connected to a server that manages all players and entities in the game world.
- **UDP Protocol**: The game uses fast UDP connections to communicate with the server. This means low latency for better real-time performance but with some packet loss tolerance.

---

### **2. Basic Controls**

Once you're connected to the game, you can control your player using the following keys to move around:

- **Up**: Move your character upwards (0x02 command sent to the server).
- **Down**: Move your character downwards.
- **Left**: Move your character left.
- **Right**: Move your character right.

Your inputs are instantly sent to the server, which processes the movement and sends back the updated positions of all players.

---

### **3. Player Actions**

- **Join the Game**: Upon joining, your player is created on the server (0x01 message). The server sends back your player’s details, and you will see yourself on the screen.
- **Control Your Character**: Use the arrow keys or assigned input keys to move your character around the map. The server processes your actions and updates your position for all players to see.
- **Interact with Other Players**: You will see other players in the game world. Their movements and actions are also processed and broadcasted by the server.

---

### **4. Gameplay Elements**

- **Enemies**: Enemies will spawn in the game. The server will broadcast their movements to all players. Your goal is to avoid or destroy them using your in-game abilities.
- **Missiles and Attacks**: You can attack enemies by shooting missiles (handled by the server). Each time you shoot, a message is sent to the server, which handles the collision and updates the enemy's status.
- **Coins**: Collect in-game coins that appear on the map. These are randomly spawned by the server and picking them up will boost your score.
- **Health and Score**: The server keeps track of your health and score. You will be notified when your health decreases due to enemy hits or when your score increases as you collect coins or defeat enemies.

---

### **5. Multiplayer Interactions**

- **Disconnections**: If a player disconnects, the server will notify all remaining players (with 0x04). The player will be removed from the game world.
- **Player Death**: If your player dies (health reaches 0), the server will broadcast your death to all other players. You will have to wait for a respawn to rejoin the game.
- **Score Leaderboard**: The server keeps track of all players' scores. You can see your rank compared to other players during the game.

---

### **6. Game Objectives**

- **Survival**: Stay alive by avoiding enemy attacks and hazards. Your health will decrease if you get hit.
- **High Score**: Collect coins and defeat enemies to increase your score. Compete with other players to reach the top of the leaderboard.
- **Cooperation or Competition**: Depending on the game mode, you can either team up with other players to fight enemies or compete against them for the highest score.

---

### **7. Game Status Updates**

The server sends regular updates to all clients, including:

- **New Player Positions**: Whenever a player moves, all clients receive updated position data.
- **Enemy and Object Positions**: The server broadcasts new enemy and object locations, which you need to avoid or interact with.
- **Player Deaths and Disconnections**: Receive real-time notifications if a player disconnects or dies during gameplay.

---

Now that you know the basics, jump in and enjoy the game! Stay sharp, coordinate with your teammates, and aim for the top score!