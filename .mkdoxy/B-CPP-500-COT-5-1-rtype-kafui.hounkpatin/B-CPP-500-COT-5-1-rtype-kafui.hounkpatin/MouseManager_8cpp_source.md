

# File MouseManager.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Mouse**](dir_6b283f0e52bc253c2977cc1de7c30b9b.md) **>** [**MouseManager.cpp**](MouseManager_8cpp.md)

[Go to the documentation of this file](MouseManager_8cpp.md)


```C++
#include "../../../include/Engine/Mouse/MouseManager.hpp"

MouseManager::MouseManager() {}

MouseManager::~MouseManager() {}

void MouseManager::handleMousePosition(sf::RenderWindow &window) {
  sf::Vector2i mousePosition = sf::Mouse::getPosition(window);
  x = mousePosition.x;
  y = mousePosition.y;
  // std::cout << "position x = " << mousePosition.x << " y = " <<
  // mousePosition.y << std::endl;
}

float MouseManager::getMouseX() const { return x; }

float MouseManager::getMouseY() const { return y; }
```


