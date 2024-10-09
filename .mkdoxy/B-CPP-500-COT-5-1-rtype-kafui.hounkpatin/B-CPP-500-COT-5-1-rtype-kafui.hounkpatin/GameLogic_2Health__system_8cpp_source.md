

# File Health\_system.cpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Health\_system.cpp**](GameLogic_2Health__system_8cpp.md)

[Go to the documentation of this file](GameLogic_2Health__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Health_system.cpp
*/

#include "Health_system.hpp"

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


