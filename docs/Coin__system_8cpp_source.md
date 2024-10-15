

# File Coin\_system.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Coin\_system.cpp**](Coin__system_8cpp.md)

[Go to the documentation of this file](Coin__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Coin_system.cpp
*/

#include "../../include/Server/Coin_system.hpp"

void CoinSystem::checkCoins(Registry &registry)
{
    auto &coins = registry.get_entities("Coin");
    auto &players = registry.get_entities("Player");
    int coinCollected = 0;

    for (auto &coin : coins)
    {
        if (!coin->_alive)
        {
            coinCollected++;
        }
    }

    for (auto &player : players)
    {
        player->score->set_score(coinCollected * 10);
    }
}
```


