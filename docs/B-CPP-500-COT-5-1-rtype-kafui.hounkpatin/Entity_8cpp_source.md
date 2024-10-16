

# File Entity.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**Entity.cpp**](Entity_8cpp.md)

[Go to the documentation of this file](Entity_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-bsrtype-kafui.hounkpatin
** File description:
** Entity.cpp
*/

#include "../../include/Server/Entity.hpp"

void Registry::entity_update()
{
    for (auto &entity : _new_entities)
    {
        if (entity == nullptr || !entity->_alive)
            continue;

        _entities_vector.push_back(entity);
        _entities_map[entity->_tag].push_back(entity);
    }
    _new_entities.clear();
    _entities_vector.erase(std::remove_if(_entities_vector.begin(), _entities_vector.end(),
                                          [](const std::shared_ptr<Entity> &entity)
                                          { return entity == nullptr || !entity->_alive; }),
                           _entities_vector.end());
    for (auto &pair : _entities_map)
    {
        auto &entities = pair.second;
        entities.erase(std::remove_if(entities.begin(), entities.end(),
                                      [](const std::shared_ptr<Entity> &entity)
                                      { return entity == nullptr || !entity->_alive; }),
                       entities.end());
    }
}

EntityVector &Registry::get_entities(const std::string tag)
{
    return _entities_map[tag];
}

EntityVector &Registry::get_entities()
{
    return _entities_vector;
}

Vector2D Registry::spawn_enemy()
{
    auto enemy = add_entity("Enemy");
    enemy->transform = std::make_unique<Transform>(Vector2D(200, 200), Vector2D(0, 0));
    enemy->bbox = std::make_unique<BBox>(Vector2D(100, 100));
    enemy->transform->position.y = rand() % 700 + 100;
    enemy->transform->position.x = 1370;
    enemy->health = std::make_unique<Health>(10);
    return enemy->transform->position;
}

std::shared_ptr<Entity> Registry::add_entity(const std::string tag)
{
    std::shared_ptr<Entity> entity = std::make_unique<Entity>(_entities_count, tag);
    _new_entities.push_back(entity);
    _entities_count++;
    return entity;
}

void Registry::spawn_coin()
{
    auto coin = add_entity("Coin");
    coin->transform = std::make_unique<Transform>(Vector2D(200, 200), Vector2D(0, 0));
    coin->bbox = std::make_unique<BBox>(Vector2D(20, 20));
    coin->transform->position.y = rand() % 400 + 100;
    coin->transform->position.x = 775;
    coin->transform->velocity.x = -0.005;
}

void Registry::spawn_player(std::string name)
{
    auto player = add_entity("Player");
    // entity_update();
    auto players = get_entities("Player");
    std::cout << "Players size : " << players.size() << std::endl;
    if (players.size() == 0)
        player->transform = std::make_unique<Transform>(Vector2D(100, 100), Vector2D(0, 0));
    if (players.size() == 1)
        player->transform = std::make_unique<Transform>(Vector2D(100, 300), Vector2D(0, 0));
    player->bbox = std::make_unique<BBox>(Vector2D(50, 50));
    player->health = std::make_unique<Health>(100);
    player->score = std::make_unique<Score>();
    player->input = std::make_unique<Input>();
    player->name = std::make_unique<Name>(name);
}

void Registry::spawn_boss()
{
    auto boss = add_entity("Boss");
    boss->transform = std::make_unique<Transform>(Vector2D(200, 200), Vector2D(0, 0));
    boss->bbox = std::make_unique<BBox>(Vector2D(100, 100));
    boss->transform->position.y = rand() % 400 + 100;
    boss->transform->position.x = 775;
    boss->health = std::make_unique<Health>(100);
    boss->score = std::make_unique<Score>();
    boss->input = std::make_unique<Input>();
    boss->name = std::make_unique<Name>("Boss");
}
```


