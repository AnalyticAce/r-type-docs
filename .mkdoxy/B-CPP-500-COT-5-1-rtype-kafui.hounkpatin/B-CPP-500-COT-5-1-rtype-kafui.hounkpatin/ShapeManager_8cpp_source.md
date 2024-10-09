

# File ShapeManager.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Shape**](dir_430e7e5a0f7cd3d6a7efc744827f42b5.md) **>** [**ShapeManager.cpp**](ShapeManager_8cpp.md)

[Go to the documentation of this file](ShapeManager_8cpp.md)


```C++
#include "../../../include/Engine/Shape/ShapeManager.hpp"

ShapeManager::ShapeManager() {}

ShapeManager::~ShapeManager() {}

void ShapeManager::drawRectangle(sf::RenderWindow &window, float x, float y,
                                 float width, float height,
                                 const sf::Color &color, float thickness = 1) {
  sf::RectangleShape rectangle(sf::Vector2f(width, height));
  rectangle.setPosition(x, y);
  rectangle.setFillColor(color);
  rectangle.setOutlineThickness(thickness);
  window.draw(rectangle);
}

void ShapeManager::drawCircle(sf::RenderWindow &window, float x, float y,
                              float radius, const sf::Color &color,
                              float thickness = 1) {
  sf::CircleShape circle(radius);
  circle.setPosition(x, y);
  circle.setFillColor(color);
  circle.setOutlineThickness(thickness);
  window.draw(circle);
}
```


