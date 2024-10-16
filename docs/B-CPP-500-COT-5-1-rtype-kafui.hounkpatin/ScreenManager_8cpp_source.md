

# File ScreenManager.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**ScreenManager.cpp**](ScreenManager_8cpp.md)

[Go to the documentation of this file](ScreenManager_8cpp.md)


```C++
#include "ScreenManager.hpp"

GameUI::ScreenManager::ScreenManager(sf::RenderWindow &window) : window(window)
{
}

void GameUI::ScreenManager::switchToScreen(const std::string &name)
{
    auto it = screens.find(name);
    if (it != screens.end())
    {
        currentScreen = it->second();
    }
}

void GameUI::ScreenManager::update()
{
    if (currentScreen)
    {
        currentScreen->update();
    }
}

void GameUI::ScreenManager::render()
{
    if (currentScreen)
    {
        currentScreen->render(window);
    }
}

void GameUI::ScreenManager::handleEvent(sf::Event &event)
{
    if (currentScreen)
    {
        currentScreen->handleEvent(event);
    }
}
```


