

# File GameSetting.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GameSetting.cpp**](GameSetting_8cpp.md)

[Go to the documentation of this file](GameSetting_8cpp.md)


```C++
#include "GameSetting.hpp"

GameUI::GameSetting::GameSetting(ScreenManager &screenManager) : screenManager(screenManager)
{
    if (!font.loadFromFile("assets/font/Bangers.ttf"))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}

bool GameUI::GameSetting::setGameSetting(const std::string &filePath, float windowWidth,
                                         float windowHeight)
{
    if (GameSettingImage.createImage(filePath))
    {
        GameSettingImage.fitToScreen(windowWidth / 2, windowHeight / 2);
        centerImage(GameSettingImage, windowWidth, windowHeight);
        return true;
    }
    else
    {
        std::cerr << "Failed to load GameSetting image." << std::endl;
        return false;
    }
}

bool GameUI::GameSetting::setBackground(const std::string &filePath, float windowWidth,
                                        float windowHeight)
{
    if (backgroundImage.createImage(filePath))
    {
        backgroundImage.fitToScreen(windowWidth, windowHeight);
        return true;
    }
    else
    {
        std::cerr << "Failed to load background image." << std::endl;
        return false;
    }
}

void GameUI::GameSetting::drawBackground(sf::RenderWindow &window)
{
    window.draw(getBackgroundSprite());
}

void GameUI::GameSetting::drawGameSetting(sf::RenderWindow &window)
{
    window.draw(getGameSettingSprite());
}

const sf::Sprite &GameUI::GameSetting::getGameSettingSprite() const
{
    return GameSettingImage.getSprite();
}

const sf::Sprite &GameUI::GameSetting::getBackgroundSprite() const
{
    return backgroundImage.getSprite();
}

void GameUI::GameSetting::centerImage(ImageManager &img, float windowWidth, float windowHeight)
{
    sf::Sprite &sprite = img.getSprite();
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}

void GameUI::GameSetting::shapebuilder(sf::RenderWindow &window)
{
    // this->rect1 = shapeManager1.drawRectangle(window, 592, 366, 180, 50,
    // sf::Color::Blue, 5, true); sf::FloatRect textBounds =
    // textip.getLocalBounds(); textip.setOrigin(textBounds.left +
    // textBounds.width / 2.0f, textBounds.top + textBounds.height / 2.0f);
    // textip.setPosition(rect1.getPosition().x + rect1.getSize().x / 2.0f,
    // rect1.getPosition().y + rect1.getSize().y / 2.0f); window.draw(textip);

    // this->rect2 = shapeManager2.drawRectangle(window, 596, 501, 180, 50,
    // sf::Color::Red, 5); sf::FloatRect textBounds2 = textname.getLocalBounds();
    // textname.setOrigin(textBounds2.left + textBounds2.width / 2.0f,
    // textBounds2.top + textBounds2.height / 2.0f);
    // textname.setPosition(rect2.getPosition().x + rect2.getSize().x / 2.0f,
    // rect2.getPosition().y + rect2.getSize().y / 2.0f);
}

void GameUI::GameSetting::loadFont(const std::string &fontPath)
{
    if (!font.loadFromFile(fontPath))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}

void GameUI::GameSetting::update()
{
}

void GameUI::GameSetting::render(sf::RenderWindow &window)
{
    window.clear();

    float windowWidth = window.getSize().x;
    float windowHeight = window.getSize().y;
    if (setBackground("assets/image/Background/seamful_background.png", windowWidth, windowHeight))
    {
        drawBackground(window);
    }
    else
    {
        std::cerr << "Failed to set background" << std::endl;
    }

    if (setGameSetting("assets/image/Element/setting.png", windowWidth, windowHeight))
    {
        drawGameSetting(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    shapebuilder(window);
    window.display();
}

void GameUI::GameSetting::handleEvent(sf::Event &event)
{
    if (event.type == sf::Event::MouseButtonPressed)
    {
        sf::Vector2f mousePos = sf::Vector2f(event.mouseButton.x, event.mouseButton.y);
        std::cout << "x: " << mousePos.x << " y: " << mousePos.y << std::endl;

        // if
        // (getRect2().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        // {
        //     std::cout << "Button clicked 2" << std::endl;
        //     getButtonSound().playSound("assets/audio/Effect/button.mp3");
        //     sf::sleep(sf::seconds(0.5));
        //     screenManager.switchToScreen("GameSetting");
        // }
    }
}
```


