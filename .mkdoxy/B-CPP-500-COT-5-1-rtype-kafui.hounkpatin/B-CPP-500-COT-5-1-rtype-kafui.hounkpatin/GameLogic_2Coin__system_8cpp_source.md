

# File Coin\_system.cpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Coin\_system.cpp**](GameLogic_2Coin__system_8cpp.md)

[Go to the documentation of this file](GameLogic_2Coin__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Coin_system.cpp
*/

#include "Coin_system.hpp"

void CoinSystem::checkCoins(Registry &registry) {
  auto &coins = registry.get_entities("Coin");
  auto &players = registry.get_entities("Player");
  int coinCollected = 0;

  for (auto &coin : coins) {
    if (!coin->_alive) {
      coinCollected++;
    }
  }

  for (auto &player : players) {
    player->score->set_score(coinCollected * 10);
  }
}
```


