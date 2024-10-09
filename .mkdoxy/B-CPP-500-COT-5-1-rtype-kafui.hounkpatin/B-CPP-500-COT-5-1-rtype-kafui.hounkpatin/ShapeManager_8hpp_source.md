

# File ShapeManager.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Shape**](dir_d430bb2cf01387b823ae007b3e5a1c3c.md) **>** [**ShapeManager.hpp**](ShapeManager_8hpp.md)

[Go to the documentation of this file](ShapeManager_8hpp.md)


```C++
#ifndef SHAPEMANAGER_HPP
#define SHAPEMANAGER_HPP

#include <SFML/Graphics.hpp>
#include <iostream>

class ShapeManager {
public:
  ShapeManager();

  ~ShapeManager();

  void drawRectangle(sf::RenderWindow &window, float x, float y, float width,
                     float height, const sf::Color &color, float thickness);

  void drawCircle(sf::RenderWindow &window, float x, float y, float radius,
                  const sf::Color &color, float thickness);

private:
  // Private data members for managing internal state could be added here.
};

#endif // SHAPEMANAGER_HPP
```


