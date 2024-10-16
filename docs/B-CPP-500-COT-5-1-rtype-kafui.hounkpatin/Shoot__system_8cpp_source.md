

# File Shoot\_system.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Shoot\_system.cpp**](Shoot__system_8cpp.md)

[Go to the documentation of this file](Shoot__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Shoot_system.cpp
*/

#include "../../include/Server/Shoot_system.hpp"

Vector2D ShootSystem::spawn_projectile(Registry &registry, Entity &player)
{
    auto proj = registry.add_entity("Projectile");
    proj->transform = std::make_unique<Transform>(Vector2D(200, 200), Vector2D(0.05f, 0));
    proj->bbox = std::make_unique<BBox>(Vector2D(50, 50));
    proj->transform->position.y = player.transform->position.y + (player.bbox->size.y / 2);
    proj->transform->position.x = player.transform->position.x + (player.bbox->size.x / 2);
    registry.entity_update();
    std::cout << "Projectile spawned at: (" << proj->transform->position.x << ", "
              << proj->transform->position.y << ")" << std::endl;
    return proj->transform->position;
}
```


