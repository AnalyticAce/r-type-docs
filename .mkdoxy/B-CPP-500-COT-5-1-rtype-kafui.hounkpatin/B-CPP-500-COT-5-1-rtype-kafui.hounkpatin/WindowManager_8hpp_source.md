

# File WindowManager.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Window**](dir_9e6b83ddf0d374080d4a6053f7ebb47f.md) **>** [**WindowManager.hpp**](WindowManager_8hpp.md)

[Go to the documentation of this file](WindowManager_8hpp.md)


```C++
#ifndef HEADER_HPP
#define HEADER_HPP

#include <iostream>
#include <SFML/Graphics.hpp>
#include "../../../src/Client/Setting/Setting.hpp"

class WindowManager {
private:
  sf::RenderWindow window;
  sf::Font font;
  sf::Event event;
  Setting settings;

public:
  WindowManager(int width, int height, const std::string &windowName);
  void keepOpen();
  void render();
  void loadFont(const std::string &fontPath);
  void handleEvent();
  void drawTextTemporarily(const std::string &text, float x, float y,
                          sf::Color color, float duration);

  sf::RenderWindow &GetWindow();
};

#endif
```


