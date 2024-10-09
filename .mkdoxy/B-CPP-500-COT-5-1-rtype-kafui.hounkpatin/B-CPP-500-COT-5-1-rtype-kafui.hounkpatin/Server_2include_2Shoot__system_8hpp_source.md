

# File Shoot\_system.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Shoot\_system.hpp**](Server_2include_2Shoot__system_8hpp.md)

[Go to the documentation of this file](Server_2include_2Shoot__system_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Shoot_system.hpp
*/

#ifndef SHOOT_SYSTEM_HPP_
#define SHOOT_SYSTEM_HPP_
#include "Entity.hpp"

class Registry;

class ShootSystem {
public:
  void spawn_projectile(Registry &registry, Entity &player) {
    if (player.input->shoot == true) {
      auto proj = registry.add_entity("Projectile");
      // proj->transform =
      //     std::make_unique<Transform>(Vector2D(200, 200), Vector2D(0.05f, 0));
      // proj->cirshape = std::make_unique<CirShape>(5, 30, sf::Color::Red,
      //                                             sf::Color::Yellow, 2);
      proj->bbox = std::make_unique<BBox>(Vector2D(10, 10));
      proj->transform->position.y =
          player.transform->position.y + (player.bbox->size.y / 2);
      proj->transform->position.x =
          player.transform->position.x + (player.transform->position.x / 2);
    }
  }
};
#endif // SHOOT_SYSTEM_HPP_
```


