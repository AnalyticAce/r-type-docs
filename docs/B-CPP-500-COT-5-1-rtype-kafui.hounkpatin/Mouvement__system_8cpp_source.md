

# File Mouvement\_system.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Mouvement\_system.cpp**](Mouvement__system_8cpp.md)

[Go to the documentation of this file](Mouvement__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Mouvement_system.cpp
*/

#include "../../include/Server/Mouvement_system.hpp"

void MouvementSystem::handleInput(Registry &registry, std::string move_direction, std::string name)
{
    auto &players = registry.get_entities("Player");
    if (players.empty())
        return;
    for (auto &player : players)
    {
        player->input->reset();
        if (!player->transform || !player->bbox)
            return;
        auto &input = player->input;
        if (player->name->name == name)
        {
            if (move_direction == "keyup")
                input->up = true;
            if (move_direction == "keydown")
                input->down = true;
            if (move_direction == "keyleft")
                input->left = true;
            if (move_direction == "keyright")
                input->right = true;
            if (move_direction == "shoot")
                input->shoot = true;
        }
    }
}

Vector2D MouvementSystem::move_player(Registry &registry, std::string name)
{
    auto &players = registry.get_entities("Player");
    if (players.empty())
        return {0, 0};
    for (auto &player : players)
    {
        if (!player->transform || !player->bbox)
            return {0, 0};
        if (player->name->name == name)
        {
            player->transform->velocity = Vector2D(0, 0);
            if (player->input->up)
                player->transform->velocity.y = -5;
            if (player->input->down)
                player->transform->velocity.y = 5;
            if (player->input->left)
                player->transform->velocity.x = -5;
            if (player->input->right)
                player->transform->velocity.x = 5;

            Vector2D newPosition = player->transform->position - player->transform->velocity;
            if (newPosition.x < 0)
                newPosition.x = 0;
            if (newPosition.y < 0)
                newPosition.y = 0;
            std::cout << "Player " << name << " moved to: (" << newPosition.x << ", "
                      << newPosition.y << ")" << std::endl;
            return newPosition;
        }
    }
    return {0, 0};
}

void MouvementSystem::system_movement(EntityVector &entities)
{
    for (auto &entity : entities)
    {
        if (entity->transform)
        {
            entity->transform->position = entity->transform->position + entity->transform->velocity;
            if (entity->transform->position.x < 0)
                entity->transform->position.x = 0;
            if (entity->transform->position.y < 0)
                entity->transform->position.y = 0;
        }
    }
}

Vector2D MouvementSystem::enemy_move(Registry &registry)
{
    auto enemies = registry.get_entities("Enemy");

    for (auto enemy : enemies)
    {
        enemy->transform->velocity = Vector2D(0, 0);
        enemy->transform->velocity.x = -5;
        return (enemy->transform->position - enemy->transform->velocity);
    }
    return {0, 0};
}
```


