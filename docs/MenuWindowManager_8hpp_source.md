

# File MenuWindowManager.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Save**](dir_7f2caee7a039a4df72b6a79e2fa54694.md) **>** [**MenuWindowManager.hpp**](MenuWindowManager_8hpp.md)

[Go to the documentation of this file](MenuWindowManager_8hpp.md)


```C++
#ifndef HEADER_HPP
#define HEADER_HPP
#include <iostream>

#include "../../include/Engine/Animation/Animation.hpp"
#include "../../include/Engine/Input/InputManager.hpp"
#include "../../include/Engine/Mouse/MouseManager.hpp"

struct TemporaryText
{
    sf::Text text;
    sf::Clock clock;
    float duration;
};

class WindowManager
{
private:
    sf::RenderWindow window;
    sf::Font font;
    sf::Event event;
    InputManager input;
    MouseManager mouse;
    std::vector<TemporaryText> tempTexts;
    Animation animation;

public:
    WindowManager(int width, int height, const std::string &windowName);
    void keepOpen();
    void drawText(const std::string &text, float x, float y, sf::Color color);
    void loadFont(const std::string &fontPath);
    void render();
    void handleEvent();
    void SetWindowSize(const sf::Vector2u &size);
    sf::RenderWindow &GetWindow();
};

#endif
```


