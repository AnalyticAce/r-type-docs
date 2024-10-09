

# File main.cpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**main.cpp**](main_8cpp.md)

[Go to the documentation of this file](main_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** main.cpp
*/

#include "Coin_system.hpp"
#include "Collision_system.hpp"
#include "Entity.hpp"
#include "Health_system.hpp"
#include "Mouvement_system.hpp"
#include "Shoot_system.hpp"
#include "Time_manager.hpp"
int main() {
  Registry registry;
  sf::RenderWindow window(sf::VideoMode(800, 600), "Entity Control");
  registry.spawn_player("Test");
  registry.entity_update();
  auto player = registry.get_entities("Player")[0];
  TimeManager coinTimer;
  TimeManager spawn_coin_timer;
  CoinSystem coinSystem;
  TimeManager healthTimer;
  TimeManager enemyTimer;
  HealthSystem healthSystem;
  MouvementSystem movement;
  collision_system collision;
  TimeManager shootTimer;
  ShootSystem shootSystem;

  while (window.isOpen()) {
    registry.entity_update();
    sf::Event event;
    while (window.pollEvent(event)) {
      if (event.type == sf::Event::Closed)
        window.close();
    }
    movement.handleInput(*player->input);
    window.clear();
    if (coinTimer.getElapsedTimeInSeconds() >= 1.0f) {
        coinSystem.checkCoins(registry);
        coinTimer.restart();
    }
    if (healthTimer.getElapsedTimeInSeconds() >= 2.0f) {
        healthSystem.checkHealth(registry);
        healthTimer.restart();
    }
    if (enemyTimer.getElapsedTimeInSeconds() >= 2.0f) {
        registry.spawn_enemy();
        enemyTimer.restart();
    }
    if (spawn_coin_timer.getElapsedTimeInSeconds() >= 7.0f) {
        //registry.spawn_coin();
        spawn_coin_timer.restart();
    }
    if (shootTimer.getElapsedTimeInSeconds() >= 3.0f) {
        //std::cout << "Shooting!!!!!!!!!" << std::endl;
        shootSystem.spawn_projectile(registry, *player);
        shootTimer.restart();
    }
    for (auto& enemy : registry.get_entities("Enemy")) {
        enemy->transform->velocity = Vector2D(0, 0);
        enemy->transform->velocity.x = -0.01;
        if (enemy->transform->position.x <= 0 || enemy->transform->position.x
        >= 800 || enemy->health->currentHealth <= 0) {
            enemy->_alive = false;
        }
    }
    for (auto coin : registry.get_entities("Coin")) {
        if (coin->transform->position.x <= 0 || coin->transform->position.x
        >= 800) {
            coin->_alive = false;
        }
    }
    for (auto proj : registry.get_entities("Projectile")) {
        //proj->transform->velocity.x -= 0.01;     
        if (proj->transform->position.x >= 800) {
            proj->_alive = false;
        }
    }
    movement.move_player(registry, player->name->name);
    collision.collison_player_coins(registry);
    movement.system_movement(registry.get_entities());
    collision.collision_player_enemy(registry);
    collision.collision_enemy_projectiles(registry);
    for (auto &entity : registry.get_entities()) {
      if (entity->cirshape) {
        entity->cirshape->shape.setPosition(entity->transform->position.x,
                                            entity->transform->position.y);
        window.draw(entity->cirshape->shape);
      }
      if (entity->rectshape) {
        entity->rectshape->shape.setPosition(entity->transform->position.x,
                                             entity->transform->position.y);
        window.draw(entity->rectshape->shape);
      }
    }
    window.display();
  }
}
```


