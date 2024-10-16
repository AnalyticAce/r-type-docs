

# File GameSetting.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GameSetting.hpp**](GameSetting_8hpp.md)

[Go to the documentation of this file](GameSetting_8hpp.md)


```C++
#pragma once
#include "ScreenManager.hpp"

namespace GameUI
{
    class GameSetting : public IScreen
    {
    private:
        sf::Font font;
        std::string input;
        ImageManager GameSettingImage, backgroundImage;
        AudioManager ButtonSound;
        MouseManager mouse;
        sf::Text textip, textname;
        sf::RectangleShape rect1, rect2;
        ShapeManager shapeManager1, shapeManager2;
        void centerImage(ImageManager &img, float windowWidth, float windowHeight);
        ScreenManager &screenManager;

    public:
        GameSetting(ScreenManager &screenManager);
        void render(sf::RenderWindow &window) override;
        void update() override;
        void loadFont(const std::string &fontPath);
        void handleEvent(sf::Event &event) override;

        bool setBackground(const std::string &filePath, float windowWidth, float windowHeight);
        bool setGameSetting(const std::string &filePath, float windowWidth, float windowHeight);

        void drawGameSetting(sf::RenderWindow &window);
        void drawBackground(sf::RenderWindow &window);

        const sf::Sprite &getGameSettingSprite() const;
        const sf::Sprite &getBackgroundSprite() const;

        void shapebuilder(sf::RenderWindow &window);

        sf::RectangleShape &getRect1() { return rect1; }
        sf::RectangleShape &getRect2() { return rect2; }

        AudioManager &getButtonSound() { return ButtonSound; }
    };

} // namespace GameUI
```


