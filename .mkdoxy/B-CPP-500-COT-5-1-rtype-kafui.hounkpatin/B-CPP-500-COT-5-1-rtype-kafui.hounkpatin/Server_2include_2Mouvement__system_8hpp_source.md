

# File Mouvement\_system.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Mouvement\_system.hpp**](Server_2include_2Mouvement__system_8hpp.md)

[Go to the documentation of this file](Server_2include_2Mouvement__system_8hpp.md)


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
class MouvementSystem{
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


