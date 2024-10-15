

# File MenuWindowManager.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Save**](dir_7f2caee7a039a4df72b6a79e2fa54694.md) **>** [**MenuWindowManager.cpp**](MenuWindowManager_8cpp.md)

[Go to the documentation of this file](MenuWindowManager_8cpp.md)


```C++
#include "MenuWindowManager.hpp"

WindowManager::WindowManager(int width, int height, const std::string &windowName)
    : window(sf::VideoMode(width, height), windowName)

{
}

void WindowManager::keepOpen()
{
    animation.setPosition("red", 100.0f, 200.0f);
    animation.setPosition("gray", 300.0f, 400.0f);

    while (window.isOpen())
    {
        animation.update("red");
        animation.update("gray");
        handleEvent();
        render();
    }
}

void WindowManager::loadFont(const std::string &fontPath)
{
    if (!font.loadFromFile(fontPath))
    {
    }
}

void WindowManager::SetWindowSize(const sf::Vector2u &size)
{
    if (size.x == 0 || size.y == 0)
    {
        window.create(sf::VideoMode::getDesktopMode(), "Game Menu", sf::Style::Fullscreen);
    }
    else
    {
        window.setSize(size);
    }
}

void WindowManager::render()
{
    window.clear(sf::Color::Black);
    window.display();
}

void WindowManager::handleEvent()
{
    while (window.pollEvent(event))
    {
        if (event.type == sf::Event::Closed)
        {
            window.close();
        }
    }
}

sf::RenderWindow &WindowManager::GetWindow()
{
    return this->window;
}
```


