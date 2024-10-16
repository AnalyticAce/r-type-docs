

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

class Transform {
public:
    Vector2D position; 
    Vector2D velocity; 

    Transform() : position(0, 0), velocity(0, 0) {}

    Transform(Vector2D pos, Vector2D vel) : position(pos), velocity(vel) {}
};

class Name {
public:
    std::string name; 

    Name() : name("") {}

    Name(std::string n) : name(n) {}
};

class BBox {
public:
    Vector2D size; 

    BBox() : size(0, 0) {}

    BBox(Vector2D s) : size(s) {}
};

class Input {
public:
    bool up;    
    bool down;  
    bool left;  
    bool right; 
    bool shoot; 

    Input() : up(false), down(false), left(false), right(false), shoot(false) {}

    void reset() {
        up = down = left = right = shoot = false;
    }
};

class Health {
public:
    int maxHealth;     
    int currentHealth; 

    Health() : maxHealth(0), currentHealth(0) {}

    Health(int maxHp) : maxHealth(maxHp), currentHealth(maxHp) {}

    void takeDamage(int damage) {
        currentHealth = std::max(0, currentHealth - damage);
    }
};

class Score {
private:
    int scoreValue; 

public:
    Score() : scoreValue(0) {}

    void set_score(int new_score) {
        scoreValue += new_score;
    }

    int getScore() const {
        return scoreValue;
    }
};

class Entity {
public:
    std::unique_ptr<Transform> transform; 
    std::unique_ptr<Name> name;           
    std::unique_ptr<BBox> bbox;           
    std::unique_ptr<Input> input;         
    std::unique_ptr<Health> health;       
    std::unique_ptr<Score> score;         

    const size_t _id;           
    const std::string _tag;     
    bool _alive = true;         

    Entity(size_t id, std::string tag) : _id(id), _tag(tag) {}

    void destroy() { _alive = false; }
};

class Registry {
private:
    EntityMap _entities_map;       
    EntityVector _entities_vector; 
    EntityVector _new_entities;    
    size_t _entities_count = 0;    

public:
    std::shared_ptr<Entity> add_entity(const std::string tag);

    EntityVector& get_entities(const std::string tag);

    void remove_entity(const size_t id);
};

#endif // !ENTITY_HPP_
```


