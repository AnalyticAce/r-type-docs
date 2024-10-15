

# File Collision\_system.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Collision\_system.cpp**](Collision__system_8cpp.md)

[Go to the documentation of this file](Collision__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** CollisionSystem.cpp
*/

#include "../../include/Server/Collision_system.hpp"

void CollisionSystem::collision_player_enemy(Registry &registry)
{
    auto &players = registry.get_entities("Player");
    auto &enemies = registry.get_entities("Enemy");

    if (players.empty() || enemies.empty())
        return;

    for (auto player : players)
    {
        if (!player->transform || !player->bbox)
            continue; // Ignorer si le joueur n'a pas de boîte de collision ou de
                      // transformation

        for (auto &enemy : enemies)
        {
            if (!enemy->_alive || !enemy->transform || !enemy->bbox)
                continue;
            float playerLeft = player->transform->position.x;
            float playerRight = playerLeft + player->bbox->size.x;
            float playerTop = player->transform->position.y;
            float playerBottom = playerTop + player->bbox->size.y;

            float enemyLeft = enemy->transform->position.x;
            float enemyRight = enemyLeft + enemy->bbox->size.x;
            float enemyTop = enemy->transform->position.y;
            float enemyBottom = enemyTop + enemy->bbox->size.y;

            if (playerRight > enemyLeft && playerLeft < enemyRight && playerBottom > enemyTop &&
                playerTop < enemyBottom)
            {
                player->health->takeDamage(10);
                enemy->_alive = false;
                player->score->set_score(10);
                std::cout << "Player collided with enemy, enemy dead." << std::endl;
            }
        }
    }
    registry.entity_update();
}

void CollisionSystem::collison_player_coins(Registry &registry)
{
    auto &players = registry.get_entities("Player");
    auto &coins = registry.get_entities("Coin");
    int v = 0;
    if (players.empty())
        return;
    auto player = players[0];

    if (!player->transform || !player->bbox)
        return;

    for (auto &coin : coins)
    {
        if (!coin->transform || !coin->bbox)
            continue;

        float playerLeft = player->transform->position.x;
        float playerRight = playerLeft + player->bbox->size.x;
        float playerTop = player->transform->position.y;
        float playerBottom = playerTop + player->bbox->size.y;

        float coinLeft = coin->transform->position.x;
        float coinRight = coinLeft + coin->bbox->size.x;
        float coinTop = coin->transform->position.y;
        float coinBottom = coinTop + coin->bbox->size.y;

        if (playerRight > coinLeft && playerLeft < coinRight && playerBottom > coinTop &&
            playerTop < coinBottom)
        {
            coin->_alive = false;
        }
    }
}

bool CollisionSystem::collision_enemy_projectiles(Registry &registry)
{
    auto &projectiles = registry.get_entities("Projectile");
    auto &enemies = registry.get_entities("Enemy");

    for (auto &proj : projectiles)
    {
        for (auto &enemy : enemies)
        {
            if (check_collision(proj, enemy))
            {
                std::cout << "Projectile hit enemy!" << std::endl;
                enemy->health->takeDamage(10);
                proj->_alive = false;
                enemy->_alive = enemy->health->currentHealth > 0;
                return true;
            }
        }
    }
    return false;
}

bool CollisionSystem::check_collision(std::shared_ptr<Entity> &proj, std::shared_ptr<Entity> &enemy)
{
    float projLeft = proj->transform->position.x;
    float projRight = projLeft + proj->bbox->size.x;
    float projTop = proj->transform->position.y;
    float projBottom = projTop + proj->bbox->size.y;

    float enemyLeft = enemy->transform->position.x;
    float enemyRight = enemyLeft + enemy->bbox->size.x;
    float enemyTop = enemy->transform->position.y;
    float enemyBottom = enemyTop + enemy->bbox->size.y;

    return projRight > enemyLeft && projLeft < enemyRight && projBottom > enemyTop &&
           projTop < enemyBottom;
}
```


