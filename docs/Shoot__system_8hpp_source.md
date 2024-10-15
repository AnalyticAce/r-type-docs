

# File Shoot\_system.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Shoot\_system.hpp**](Shoot__system_8hpp.md)

[Go to the documentation of this file](Shoot__system_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Shoot_system.hpp
*/
#ifndef SHOOT_SYSTEM_HPP
#define SHOOT_SYSTEM_HPP
#include "Entity.hpp" 

class ShootSystem
{
public:
    Vector2D spawn_projectile(Registry &registry, Entity &player);
};
#endif // SHOOT_SYSTEM_HPP_
```


