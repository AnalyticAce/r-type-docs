

# File MouseManager.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Mouse**](dir_f193d769e7e735a6067828aa983bf770.md) **>** [**MouseManager.hpp**](MouseManager_8hpp.md)

[Go to the documentation of this file](MouseManager_8hpp.md)


```C++
#ifndef MOUSEMANAGER_HPP
#define MOUSEMANAGER_HPP

#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>
#include <iostream>


class MouseManager {
private:
  float x;

  float y;

public:
  MouseManager();

  ~MouseManager();

  void handleMousePosition(sf::RenderWindow &window);

  float getMouseX() const;

  float getMouseY() const;
};

#endif // MOUSEMANAGER_HPP
```


