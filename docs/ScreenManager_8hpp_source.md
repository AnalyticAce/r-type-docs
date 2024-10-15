

# File ScreenManager.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**ScreenManager.hpp**](ScreenManager_8hpp.md)

[Go to the documentation of this file](ScreenManager_8hpp.md)


```C++
#pragma once

#include <functional>
#include <memory>
#include <unordered_map>

#include "../../include/Engine/Animation/Animation.hpp"
#include "../../include/Engine/Audio/AudioManager.hpp"
#include "../../include/Engine/Image/ImageManager.hpp"
#include "../../include/Engine/Mouse/MouseManager.hpp"
#include "../../include/Engine/Shape/ShapeManager.hpp"
#include "../../include/Server/Client.hpp"
class IScreen
{
public:
    virtual void update() = 0;
    virtual void render(sf::RenderWindow &window) = 0;
    virtual void handleEvent(sf::Event &event) = 0;
    virtual ~IScreen() = default;
};

namespace GameUI
{
    class ScreenManager
    {
    public:
        ScreenManager(sf::RenderWindow &window);

        template <typename T>
        void addScreen(const std::string &name, std::function<std::unique_ptr<T>()> factory)
        {
            screens[name] = [factory]() -> std::unique_ptr<IScreen> { return factory(); };
        }

        void switchToScreen(const std::string &name);
        void update();
        void render();
        void handleEvent(sf::Event &event);
        Client client;

    private:
        sf::RenderWindow &window;
        std::unordered_map<std::string, std::function<std::unique_ptr<IScreen>()>> screens;
        std::unique_ptr<IScreen> currentScreen;
    };
} // namespace GameUI
```


