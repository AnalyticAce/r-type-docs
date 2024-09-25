# R-Type Documentation

![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black) ![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-%23008FBA.svg?style=for-the-badge&logo=cmake&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)

Welcome to the documentation for the R-Type Game Engine project. This documentation will guide you through setting up, developing, and contributing to the project.

# Introduction

## Goal of the Project
The goal of this project is to develop a multi-threaded server and a graphical client for a networked version of the classic shoot 'em up game **R-Type**, using a custom-built game engine. The project will teach advanced C++ development techniques, software engineering practices, and networked game development.

## Different Parts and Description

1. **Game Engine**: 
   - The core of the project, containing the various subsystems such as rendering, physics, audio, and more. Decoupling these subsystems is crucial for better architecture and maintainability. The engine must support a modular design and ensure optimized resource management.
   
2. **Networking**:
   - The game is networked, with multiple clients connecting to a server. The server is responsible for handling the game logic and updating the clients with the current game state. Clients communicate via UDP, and mechanisms to handle network errors, latency, and synchronization are vital.
   
3. **Game Logic**:
   - The game logic resides on the server, ensuring authoritative gameplay. It manages player actions, enemy behavior, missile trajectories, collisions, and more. Client-side logic exists for handling inputs and rendering, but the server makes the final decisions.
   
4. **Gameplay Features**:
   - Players control spaceships to battle waves of enemy Bydos. Each player can shoot missiles, and there are multiple players per game session. The game world features a scrolling background, enemies, obstacles, and player missiles, providing a rich gameplay experience.
