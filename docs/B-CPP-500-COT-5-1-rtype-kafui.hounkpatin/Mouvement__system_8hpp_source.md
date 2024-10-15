

# File Mouvement\_system.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Mouvement\_system.hpp**](Mouvement__system_8hpp.md)

[Go to the documentation of this file](Mouvement__system_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Movement_system.hpp
*/

#ifndef MOVEMENT_SYSTEM_HPP_
#define MOVEMENT_SYSTEM_HPP_
#include "Entity.hpp"

class Registry; 

class MouvementSystem
{
public:
    MouvementSystem(){};

    ~MouvementSystem(){};

    Vector2D move_player(Registry &registry, std::string name);

    void handleInput(Registry &registry, std::string move_direction, std::string name);

    void system_movement(EntityVector &entities);

    Vector2D enemy_move(Registry &registry);
};

#endif // MOVEMENT_SYSTEM_HPP_
```


