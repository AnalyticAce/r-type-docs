

# File Entity.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Entity.hpp**](Entity_8hpp.md)

[Go to the documentation of this file](Entity_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-bsrtype-kafui.hounkpatin
** File description:
** Entity.hpp
*/

#ifndef ENTITY_HPP_
#define ENTITY_HPP_
#include <any>
#include <cassert>
#include <iostream>
#include <memory>
#include <mutex>
#include <optional>
#include <string>
#include <typeindex>
#include <unordered_map>
#include <vector>

#include "Vector.hpp"

// Transform component representing position and velocity.
class Transform
{
public:
    Vector2D position = Vector2D(0, 0); 
    Vector2D velocity = Vector2D(0, 0); 

    Transform(){};

    Transform(Vector2D pos, Vector2D vel) : position(pos), velocity(vel){};
};

// Name component to store the name of an entity.
class Name
{
public:
    std::string name; 

    Name(){};

    Name(std::string n) : name(n){};
};

// BBox (Bounding Box) component representing the size of an entity.
class BBox
{
public:
    Vector2D size = Vector2D(0, 0); 

    BBox(){};

    BBox(Vector2D s) : size(s){};
};

// Input component to track player actions.
class Input
{
public:
    bool up = false;    
    bool down = false;  
    bool left = false;  
    bool right = false; 
    bool shoot = false; 

    void reset()
    {
        up = false;
        down = false;
        left = false;
        right = false;
        shoot = false;
    }
};

// Health component to track the entity's health state.
class Health
{
public:
    int maxHealth;     
    int currentHealth; 

    Health() : maxHealth(0), currentHealth(0) {}

    Health(int maxHp) : maxHealth(maxHp), currentHealth(maxHp) {}

    void takeDamage(int damage) { currentHealth = std::max(0, currentHealth - damage); }
};

// Score component to manage and track an entity's score.
class Score
{
private:
    int scoreValue = 0; 

public:
    Score() : scoreValue(0) {}

    void set_score(int new_score) { scoreValue += new_score; }

    int getScore() { return scoreValue; }
};

// Entity class representing a game object with multiple components.
class Entity
{
public:
    std::unique_ptr<Transform> transform; 
    std::unique_ptr<Name> name;           
    std::unique_ptr<BBox> bbox;           
    std::unique_ptr<Input> input;         
    std::unique_ptr<Health> health;       
    std::unique_ptr<Score> score;         

    const size_t _id = 0;               
    const std::string _tag = "Default"; 
    bool _alive = true;                 

    Entity(){};

    Entity(size_t id, std::string tag) : _id(id), _tag(tag){};

    void destroy() { _alive = false; }
};

// Typedefs for convenience.
typedef std::vector<std::shared_ptr<Entity>> EntityVector; 
typedef std::map<std::string, EntityVector> EntityMap;     

// Registry class to manage entities and their components.
class Registry
{
    EntityMap _entities_map;       
    EntityVector _entities_vector; 
    EntityVector _new_entities;    
    size_t _entities_count = 0;    

public:
    Registry(){};

    void entity_update();

    std::shared_ptr<Entity> add_entity(const std::string tag);

    EntityVector &get_entities(const std::string tag);

    EntityVector &get_entities();

    Vector2D spawn_enemy();

    void spawn_coin();

    void spawn_player(std::string name);

    void spawn_boss();

    void remove_entity(const size_t id);
};

#endif // !ENTITY_HPP_
```


