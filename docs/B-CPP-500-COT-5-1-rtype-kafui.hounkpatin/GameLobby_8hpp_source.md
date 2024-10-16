

# File GameLobby.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GameLobby.hpp**](GameLobby_8hpp.md)

[Go to the documentation of this file](GameLobby_8hpp.md)


```C++
#pragma once
#include "ScreenManager.hpp"
#define PLAY_BUTTON_X 0.432
#define PLAY_BUTTON_Y 0.53
#define SETTING_BUTTON_X 0.436
#define SETTING_BUTTON_Y 0.725

namespace GameUI
{
    class GameLobby : public IScreen
    {
    private:
        sf::Font font;
        std::string input;
        ImageManager GameLobbyImage, backgroundImage;
        ImageManager Asteriod1, Asteriod2, Asteriod3;
        AudioManager ButtonSound, RoomMusic;
        MouseManager mouse;
        sf::Text textip, textname;
        sf::RectangleShape rect1, rect2;
        ShapeManager shapeManager1, shapeManager2;
        void centerImage(ImageManager &img, float windowWidth, float windowHeight);
        ScreenManager &screenManager;

    public:
        GameLobby(ScreenManager &screenManager);
        void render(sf::RenderWindow &window) override;
        void update() override;
        void loadFont(const std::string &fontPath);
        void handleEvent(sf::Event &event) override;

        bool setBackground(const std::string &filePath, float windowWidth, float windowHeight);
        bool setGameLobby(const std::string &filePath, float windowWidth, float windowHeight);
        bool setAsteriodOne(const std::string &filePath);
        bool setAsteriodTwo(const std::string &filePath);
        bool setAsteriodThree(const std::string &filePath);
        bool setAsteriodFour(const std::string &filePath);

        void drawGameLobby(sf::RenderWindow &window);
        void drawBackground(sf::RenderWindow &window);
        void drawAsteriodOne(sf::RenderWindow &window);
        void drawAsteriodTwo(sf::RenderWindow &window);
        void drawAsteriodThree(sf::RenderWindow &window);
        void drawAsteriodFour(sf::RenderWindow &window);

        const sf::Sprite &getGameLobbySprite() const;
        const sf::Sprite &getBackgroundSprite() const;
        const sf::Sprite &getAsteriodOneSprite() const;
        const sf::Sprite &getAsteriodTwoSprite() const;
        const sf::Sprite &getAsteriodThreeSprite() const;
        const sf::Sprite &getAsteriodFourSprite() const;

        void shapebuilder(sf::RenderWindow &window);

        sf::RectangleShape &getRect1() { return rect1; }
        sf::RectangleShape &getRect2() { return rect2; }

        AudioManager &getRoomMusic() { return RoomMusic; }
        AudioManager &getButtonSound() { return ButtonSound; }
        MouseManager &getMouse() { return mouse; }
    };
} // namespace GameUI
```


