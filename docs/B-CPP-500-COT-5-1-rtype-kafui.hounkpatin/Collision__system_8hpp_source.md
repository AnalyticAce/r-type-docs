

# File Collision\_system.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Collision\_system.hpp**](Collision__system_8hpp.md)

[Go to the documentation of this file](Collision__system_8hpp.md)


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

// Forward declaration of the Registry class to avoid circular dependencies.
class Registry;

class CollisionSystem
{
public:
    CollisionSystem() {};

    ~CollisionSystem() {};

    void collision_player_enemy(Registry &registry);

    void collison_player_coins(Registry &registry);

    bool collision_enemy_projectiles(Registry &registry);

    bool check_collision(std::shared_ptr<Entity> &proj, std::shared_ptr<Entity> &enemy);
};

#endif // COLLISION_SYSTEM_HPP_
```


