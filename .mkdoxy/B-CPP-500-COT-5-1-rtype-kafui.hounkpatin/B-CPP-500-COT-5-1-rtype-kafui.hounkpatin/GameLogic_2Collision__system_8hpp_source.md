

# File Collision\_system.hpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Collision\_system.hpp**](GameLogic_2Collision__system_8hpp.md)

[Go to the documentation of this file](GameLogic_2Collision__system_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Collision_system.hpp
*/

#ifndef COLLISION_SYSTEM_HPP_
#define COLLISION_SYSTEM_HPP_
#include "Entity.hpp"

class Registry;
class collision_system {
public:
  collision_system(){};
  ~collision_system(){};
  void collision_player_enemy(Registry &registry);
  void collison_player_coins(Registry &registry);
  void collision_enemy_projectiles(Registry &registry);
  bool check_collision(std::shared_ptr<Entity> &proj,
                      std::shared_ptr<Entity> &enemy);
};
#endif // COLLISION_SYSTEM_HPP_
```


