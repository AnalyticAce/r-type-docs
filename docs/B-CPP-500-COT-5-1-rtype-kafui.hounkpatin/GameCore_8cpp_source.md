

# File GameCore.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GameCore.cpp**](GameCore_8cpp.md)

[Go to the documentation of this file](GameCore_8cpp.md)


```C++
#include "GameCore.hpp"

#include "GamePlay.hpp"
#include "GameSetting.hpp"

GameUI::GameCore::GameCore()
    : window(sf::VideoMode(BASE_WIDTH, BASE_HEIGHT), "Epitech | R-Type"), screenManager(window),
      roomLobby(screenManager)
{
    screenManager.addScreen<GameLobby>("GameLobby", [&]()
                                       { return std::make_unique<GameLobby>(screenManager); });
    screenManager.addScreen<RoomLobby>("RoomLobby", [&]()
                                       { return std::make_unique<RoomLobby>(screenManager); });
    screenManager.addScreen<GameSetting>("GameSetting", [&]()
                                         { return std::make_unique<GameSetting>(screenManager); });
    // screenManager.addScreen<GamePlay>("GamePlay",
    //                                   [&]() { return std::make_unique<GamePlay>(screenManager);
    //                                   });
    screenManager.switchToScreen("GameLobby");
}

void GameUI::GameCore::run()
{
    sf::Clock clock;

    RoomMusic.playMusic("assets/audio/Music/menu1.ogg");

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
            {
                window.close();
            }
            screenManager.handleEvent(event);
        }

        screenManager.update();

        window.clear();
        screenManager.render();
        window.display();
    }
}
```


