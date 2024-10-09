

# File Mouvement\_system.cpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Mouvement\_system.cpp**](GameLogic_2Mouvement__system_8cpp.md)

[Go to the documentation of this file](GameLogic_2Mouvement__system_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Mouvement_system.cpp
*/

#include "Mouvement_system.hpp"

void MouvementSystem::handleInput(Input &input) {
  input.reset();

  if (sf::Keyboard::isKeyPressed(sf::Keyboard::Z))
    input.up = true;
  if (sf::Keyboard::isKeyPressed(sf::Keyboard::S))
    input.down = true;
  if (sf::Keyboard::isKeyPressed(sf::Keyboard::Q))
    input.left = true;
  if (sf::Keyboard::isKeyPressed(sf::Keyboard::D))
    input.right = true;
  //if (sf::Keyboard::isKeyPressed(sf::Keyboard::Space))
    //input.shoot = true;
}

void MouvementSystem::move_player(Registry &registry, std::string name) {
  auto &players = registry.get_entities("Player");

  if (players.empty())
    return;
  for (auto &player : players) {
    if (!player->transform || !player->bbox)
      return;
    if (player->name->name == name) {
      player->transform->velocity = Vector2D(0, 0);

      if (player->input->up)
        player->transform->velocity.y = -0.005;
      if (player->input->down)
        player->transform->velocity.y = 0.005;
      if (player->input->left)
        player->transform->velocity.x = -0.005;
      if (player->input->right)
        player->transform->velocity.x = 0.005;
    }
  }
}

void MouvementSystem::system_movement(EntityVector &entities) {
  for (auto &entity : entities) {
    if (entity->transform) {
      entity->transform->position =
          entity->transform->position + entity->transform->velocity;
    }
  }
}
```


