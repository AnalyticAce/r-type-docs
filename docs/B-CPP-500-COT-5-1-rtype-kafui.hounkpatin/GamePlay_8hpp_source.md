

# File GamePlay.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GamePlay.hpp**](GamePlay_8hpp.md)

[Go to the documentation of this file](GamePlay_8hpp.md)


```C++
#pragma once
#include "ScreenManager.hpp"

namespace GameUI
{
    class GamePlay : public IScreen
    {
    private:
        sf::Font font;
        std::string input;
        ImageManager GamePlayImage, backgroundImage, TeamScoreImage, LifeBoardImage;
        AudioManager ButtonSound;
        Animation player1, player2;
        Animation enemies1, enemies2, enemies3, enemies4, enemies5, enemies6, enemies7, enemies8, enemies9, enemiesBoss;
        ShapeManager shapeManager1, shapeManager2;
        void centerImage(ImageManager &img, float windowWidth, float windowHeight);
        ScreenManager &screenManager;

    public:
        bool playIsUp, playIsDown, playIsRight, playIsLeft;
        GamePlay(ScreenManager &screenManager);
        void render(sf::RenderWindow &window) override;
        void update() override;
        void loadFont(const std::string &fontPath);
        void handleEvent(sf::Event &event) override;

        void createPlayer1();
        void createPlayer2();
        void createEnemies();
        void createEnemies2();
        void createEnemies3();
        void createEnemies4();
        void createEnamies5();
        void createEnamies6();
        void createEnamies7();
        void createEnamies8();
        void createEnamies9();
        void createEnamiesBoss();
        void spawnRandomEnemies();
        bool setBackground(const std::string &filePath, float windowWidth, float windowHeight);
        bool setTeamScore(const std::string &filePath, float windowWidth, float windowHeight);
        bool setLifeBoard(const std::string &filePath, float windowWidth, float windowHeight);

        void drawTeamScore(sf::RenderWindow &window);
        void drawBackground(sf::RenderWindow &window);
        void drawLifeBoard(sf::RenderWindow &window);

        const sf::Sprite &getTeamScoreSprite() const;
        const sf::Sprite &getBackgroundSprite() const;
        const sf::Sprite &getLifeBoardSprite() const;

        void shapebuilder(sf::RenderWindow &window);

        AudioManager &getButtonSound() { return ButtonSound; }
    };
} // namespace GameUI
```


