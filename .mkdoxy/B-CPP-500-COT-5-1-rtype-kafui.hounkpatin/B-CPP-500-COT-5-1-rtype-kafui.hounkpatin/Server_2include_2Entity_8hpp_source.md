

# File Entity.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Entity.hpp**](Server_2include_2Entity_8hpp.md)

[Go to the documentation of this file](Server_2include_2Entity_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** B-CPP-500-COT-5-1-bsrtype-kafui.hounkpatin
** File description:
** Entity.hpp
*/

#ifndef ENTITY_HPP_
#define ENTITY_HPP_
#include "Vector.hpp"
// #include <SFML/Audio.hpp>
// #include <SFML/Graphics.hpp>
// #include <SFML/Network.hpp>
// #include <SFML/System.hpp>
// #include <SFML/Window.hpp>
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

class Transform {
public:
  Vector2D position = Vector2D(0, 0);
  Vector2D velocity = Vector2D(0, 0);
  Transform(){};
  Transform(Vector2D pos, Vector2D vel) : position(pos), velocity(vel){};
};

// class CirShape {
// public:
//   sf::CircleShape shape;
//   CirShape(){};
//   CirShape(float radius, int point_count, sf::Color out_color,
//            sf::Color in_color, int thikness) {
//     shape.setRadius(radius);
//     shape.setPointCount(point_count);
//     shape.setOutlineColor(out_color);
//     shape.setFillColor(in_color);
//     shape.setOutlineThickness(thikness);
//   };
// };

// class RectShape {
// public:
//   sf::RectangleShape shape;
//   RectShape(){};
//   RectShape(float width, float height, sf::Color out_color, sf::Color in_color,
//             int thikness) {
//     shape.setSize(sf::Vector2f(width, height));
//     shape.setOutlineColor(out_color);
//     shape.setFillColor(in_color);
//     shape.setOutlineThickness(thikness);
//   };
// };

class Name {
public:
  std::string name;
  Name(){};
  Name(std::string n) : name(n){};
};

class BBox {
public:
  Vector2D size = Vector2D(0, 0);
  BBox(){};
  BBox(Vector2D s) : size(s){};
};

class Input {
public:
  bool up = false;
  bool down = false;
  bool left = false;
  bool right = false;
  bool shoot = false;

  void reset() {
    up = false;
    down = false;
    left = false;
    right = false;
    shoot = false;
  }
};

class Health {
public:
  int maxHealth;
  int currentHealth;

  Health() : maxHealth(0), currentHealth(0) {}
  Health(int maxHp) : maxHealth(maxHp), currentHealth(maxHp) {}

  void takeDamage(int damage) {
    currentHealth = std::max(0, maxHealth - damage);
  }
};

class Score {
private:
  int scoreValue = 0;

public:
  Score() : scoreValue(0) {}

  void set_score(int new_score) { scoreValue = new_score; }
  int getScore() { return scoreValue; }
};

class Entity {
public:
  std::unique_ptr<Transform> transform;
  // std::unique_ptr<CirShape> cirshape;
  // std::unique_ptr<RectShape> rectshape;
  std::unique_ptr<Name> name;
  std::unique_ptr<BBox> bbox;
  std::unique_ptr<Input> input;
  std::unique_ptr<Health> health;
  std::unique_ptr<Score> score;
  Entity(){};
  Entity(size_t id, std::string tag) : _id(id), _tag(tag){};
  const size_t _id = 0;
  const std::string _tag = "Default";
  void destroy() { _alive = false; }
  bool _alive = true;
};

typedef std::vector<std::shared_ptr<Entity>> EntityVector;
typedef std::map<std::string, EntityVector> EntityMap;

class Registry {

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
  void remove_entity(const size_t id);
};

#endif // !ENTITY_HPP_
```


