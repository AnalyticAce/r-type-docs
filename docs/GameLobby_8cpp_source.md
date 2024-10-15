

# File GameLobby.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GameLobby.cpp**](GameLobby_8cpp.md)

[Go to the documentation of this file](GameLobby_8cpp.md)


```C++
#include "GameLobby.hpp"

GameUI::GameLobby::GameLobby(ScreenManager &screenManager) : screenManager(screenManager)
{
    if (!font.loadFromFile("assets/font/Bangers.ttf"))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}

bool GameUI::GameLobby::setGameLobby(const std::string &filePath, float windowWidth,
                                     float windowHeight)
{
    if (GameLobbyImage.createImage(filePath))
    {
        GameLobbyImage.fitToScreen(windowWidth / 3.5, windowHeight / 3.5);
        centerImage(GameLobbyImage, windowWidth, windowHeight);
        return true;
    }
    else
    {
        std::cerr << "Failed to load GameLobby image." << std::endl;
        return false;
    }
}

bool GameUI::GameLobby::setBackground(const std::string &filePath, float windowWidth,
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

bool GameUI::GameLobby::setAsteriodOne(const std::string &filePath)
{
    if (Asteriod1.createImage(filePath))
    {
        Asteriod1.setPosition(103, 400);
        Asteriod1.setScale(1.5, 1.5);
        return true;
    }
    else
    {
        std::cerr << "Failed to load background image." << std::endl;
        return false;
    }
}

bool GameUI::GameLobby::setAsteriodTwo(const std::string &filePath)
{
    if (Asteriod2.createImage(filePath))
    {
        Asteriod2.setPosition(1100, 121);
        Asteriod2.setScale(1.5, 1.5);
        return true;
    }
    else
    {
        std::cerr << "Failed to load background image." << std::endl;
        return false;
    }
}

bool GameUI::GameLobby::setAsteriodThree(const std::string &filePath)
{
    if (Asteriod3.createImage(filePath))
    {
        Asteriod3.setPosition(950, 500);
        Asteriod3.setScale(1.5, 1.5);
        return true;
    }
    else
    {
        std::cerr << "Failed to load background image." << std::endl;
        return false;
    }
}

void GameUI::GameLobby::drawBackground(sf::RenderWindow &window)
{
    window.draw(getBackgroundSprite());
}

void GameUI::GameLobby::drawGameLobby(sf::RenderWindow &window)
{
    window.draw(getGameLobbySprite());
}

void GameUI::GameLobby::drawAsteriodOne(sf::RenderWindow &window)
{
    window.draw(getAsteriodOneSprite());
}

void GameUI::GameLobby::drawAsteriodTwo(sf::RenderWindow &window)
{
    window.draw(getAsteriodTwoSprite());
}

void GameUI::GameLobby::drawAsteriodThree(sf::RenderWindow &window)
{
    window.draw(getAsteriodThreeSprite());
}

const sf::Sprite &GameUI::GameLobby::getAsteriodOneSprite() const
{
    return Asteriod1.getSprite();
}

const sf::Sprite &GameUI::GameLobby::getAsteriodTwoSprite() const
{
    return Asteriod2.getSprite();
}

const sf::Sprite &GameUI::GameLobby::getAsteriodThreeSprite() const
{
    return Asteriod3.getSprite();
}

const sf::Sprite &GameUI::GameLobby::getGameLobbySprite() const
{
    return GameLobbyImage.getSprite();
}

const sf::Sprite &GameUI::GameLobby::getBackgroundSprite() const
{
    return backgroundImage.getSprite();
}

void GameUI::GameLobby::centerImage(ImageManager &img, float windowWidth, float windowHeight)
{
    sf::Sprite &sprite = img.getSprite();
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}

void GameUI::GameLobby::shapebuilder(sf::RenderWindow &window)
{
    this->rect1 = shapeManager1.drawRectangle(window, 592, 366, 180, 50, sf::Color::Red, 5);
    sf::FloatRect textBounds = textip.getLocalBounds();
    textip.setOrigin(textBounds.left + textBounds.width / 2.0f,
                     textBounds.top + textBounds.height / 2.0f);
    textip.setPosition(rect1.getPosition().x + rect1.getSize().x / 2.0f,
                       rect1.getPosition().y + rect1.getSize().y / 2.0f);
    window.draw(textip);

    this->rect2 = shapeManager2.drawRectangle(window, 596, 501, 180, 50, sf::Color::Red, 5);
    sf::FloatRect textBounds2 = textname.getLocalBounds();
    textname.setOrigin(textBounds2.left + textBounds2.width / 2.0f,
                       textBounds2.top + textBounds2.height / 2.0f);
    textname.setPosition(rect2.getPosition().x + rect2.getSize().x / 2.0f,
                         rect2.getPosition().y + rect2.getSize().y / 2.0f);
}

void GameUI::GameLobby::loadFont(const std::string &fontPath)
{
    if (!font.loadFromFile(fontPath))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}

void GameUI::GameLobby::update()
{
}

void GameUI::GameLobby::render(sf::RenderWindow &window)
{
    window.clear();

    float windowWidth = window.getSize().x;
    float windowHeight = window.getSize().y;

    if (setBackground("assets/image/Background/background1.png", windowWidth, windowHeight))
    {
        drawBackground(window);
    }
    else
    {
        std::cerr << "Failed to set background" << std::endl;
    }

    if (setGameLobby("assets/image/Element/welcome.png", windowWidth, windowHeight))
    {
        drawGameLobby(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    if (setAsteriodOne("assets/image/Asteroids/brown-large.png"))
    {
        drawAsteriodOne(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    if (setAsteriodTwo("assets/image/Asteroids/gray-medium.png"))
    {
        drawAsteriodTwo(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    if (setAsteriodThree("assets/image/Asteroids/red-small.png"))
    {
        drawAsteriodThree(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }
    shapebuilder(window);
    window.display();
}

void GameUI::GameLobby::handleEvent(sf::Event &event)
{
    if (event.type == sf::Event::MouseButtonPressed)
    {
        sf::Vector2f mousePos = sf::Vector2f(event.mouseButton.x, event.mouseButton.y);
        std::cout << "x: " << mousePos.x << " y: " << mousePos.y << std::endl;

        if (getRect1().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        {
            std::cout << "Button clicked 1" << std::endl;
            getButtonSound().playSound("assets/audio/Effect/button.mp3");
            sf::sleep(sf::seconds(0.5));
            screenManager.switchToScreen("RoomLobby");
        }
        else if (getRect2().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        {
            std::cout << "Button clicked 2" << std::endl;
            getButtonSound().playSound("assets/audio/Effect/button.mp3");
            // sf::sleep(sf::seconds(0.5));
            screenManager.switchToScreen("GameSetting");
        }
    }
}
```


