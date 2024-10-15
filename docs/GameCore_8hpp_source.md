

# File GameCore.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GameCore.hpp**](GameCore_8hpp.md)

[Go to the documentation of this file](GameCore_8hpp.md)


```C++
#pragma once
#include "GameLobby.hpp"
#include "RoomLobby.hpp"
#include "ScreenManager.hpp"

#define BASE_WIDTH 1366
#define BASE_HEIGHT 768

namespace GameUI
{
    class GameCore
    {
    public:
        GameCore();
        void run();
        RoomLobby roomLobby;

    private:
        sf::RenderWindow window;
        ScreenManager screenManager;
        AudioManager RoomMusic;
    };
} // namespace GameUI
```


