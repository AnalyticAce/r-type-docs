

# File Health\_system.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**Health\_system.cpp**](Server_2src_2Health__system_8cpp.md)

[Go to the documentation of this file](Server_2src_2Health__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Health_system.cpp
*/

#include "../include/Health_system.hpp"

void HealthSystem::checkHealth(Registry &registry) {
  auto &players = registry.get_entities("Player");
  auto &enemies = registry.get_entities("Enemy");

  size_t enemyCount = 0;
  if (players.empty())
    return;

  for (auto &enemy : enemies) {
    if (enemy->_alive == false) {
      enemyCount++;
    }
  }
  for (auto &player : players) {
    if (player->health->currentHealth > 0) {
      player->health->takeDamage(enemyCount * 10);
    }
    if (player->health->currentHealth <= 0) {
      player->_alive = false;
    }
  }
}
```


