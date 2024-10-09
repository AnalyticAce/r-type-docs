

# File Mouvement\_system.hpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Mouvement\_system.hpp**](GameLogic_2Mouvement__system_8hpp.md)

[Go to the documentation of this file](GameLogic_2Mouvement__system_8hpp.md)


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

  void move_player(Registry &registry, std::string name);
  void handleInput(Input &input);
  void system_movement(EntityVector &entities);
};
#endif // MOVEMENT_SYSTEM_HPP_
```


