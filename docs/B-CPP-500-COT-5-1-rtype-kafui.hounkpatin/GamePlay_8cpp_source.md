

# File GamePlay.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**GamePlay.cpp**](GamePlay_8cpp.md)

[Go to the documentation of this file](GamePlay_8cpp.md)


```C++
#include "GamePlay.hpp"

GameUI::GamePlay::GamePlay(ScreenManager &screenManager) : screenManager(screenManager)
{
    if (!font.loadFromFile("assets/font/Bangers.ttf"))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
    createPlayer1();
    // spawnRandomEnemies();
    createPlayer2();
    createEnemies();
    createEnemies2();
    createEnemies3();
    createEnemies4();
    createEnamies5();
    createEnamies6();
    createEnamies7();
    createEnamies8();
    createEnamies9();
}

bool GameUI::GamePlay::setBackground(const std::string &filePath, float windowWidth,
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

bool GameUI::GamePlay::setTeamScore(const std::string &filePath, float windowWidth,
                                    float windowHeight)
{
    if (TeamScoreImage.createImage(filePath))
    {
        TeamScoreImage.fitToScreen(windowWidth / 3.5, windowHeight / 3.5);
        TeamScoreImage.setPosition(100, 40);
        TeamScoreImage.setScale(0.5, 0.5);
        return true;
    }
    else
    {
        std::cerr << "Failed to load TeamScore image." << std::endl;
        return false;
    }
}

bool GameUI::GamePlay::setLifeBoard(const std::string &filePath, float windowWidth,
                                    float windowHeight)
{
    if (LifeBoardImage.createImage(filePath))
    {
        LifeBoardImage.fitToScreen(windowWidth / 3.5, windowHeight / 3.5);
        LifeBoardImage.setPosition(700, 40);
        LifeBoardImage.setScale(0.3, 0.3);
        return true;
    }
    else
    {
        std::cerr << "Failed to load LifeBoard image." << std::endl;
        return false;
    }
}

void GameUI::GamePlay::createPlayer1()
{
    player1.loadAnimation("red", 8, 1.5, 1.5);
    player1.setPosition("red", 100, 100);
}

void GameUI::GamePlay::createPlayer2()
{
    player2.loadAnimation("blue", 8, 1.5, 1.5);
    player2.setPosition("blue", 100, 200);
}


void GameUI::GamePlay::spawnRandomEnemies()
{
    // return random number between 1 and 9
    int random = rand() % 9 + 1;
    if (random == 1)
    {
        createEnemies();
    }
    else if (random == 2)
    {
        createEnemies2();
    }
    else if (random == 3)
    {
        createEnemies3();
    }
    else if (random == 4)
    {
        createEnemies4();
    }
    else if (random == 5)
    {
        createEnamies5();
    }
    else if (random == 6)
    {
        createEnamies6();
    }
    else if (random == 7)
    {
        createEnamies7();
    }
    else if (random == 8)
    {
        createEnamies8();
    }
    else if (random == 9)
    {
        createEnamies9();
    }
}


void GameUI::GamePlay::createEnemies()
{
    enemies1.loadAnimation("green", 8, 1.25, 1.25);
    enemies1.setPosition("green", 150, 150);
}

void GameUI::GamePlay::createEnemies2()
{
    enemies2.loadAnimation("yellow", 8, 1.25, 1.25);
    enemies2.setPosition("yellow", 200, 200);
}

void GameUI::GamePlay::createEnemies3()
{
    enemies3.loadAnimation("purple", 8, 1.25, 1.25);
    enemies3.setPosition("purple", 250, 250);
}

void GameUI::GamePlay::createEnemies4()
{
    enemies4.loadAnimation("orange", 5, 1.25, 1.25);
    enemies4.setPosition("orange", 300, 300);
}

void GameUI::GamePlay::createEnamies5()
{
    enemies5.loadAnimation("pink", 5, 1.25, 1.25);
    enemies5.setPosition("pink", 350, 350);
}

void GameUI::GamePlay::createEnamies6()
{
    enemies6.loadAnimation("cyan", 5, 1.25, 1.25);
    enemies6.setPosition("cyan", 400, 400);
}

void GameUI::GamePlay::createEnamies7()
{
    enemies7.loadAnimation("brown", 5, 1.25, 1.25);
    enemies7.setPosition("brown", 450, 450);
}

void GameUI::GamePlay::createEnamies8()
{
    enemies8.loadAnimation("white", 5, 1.25, 1.25);
    enemies8.setPosition("white", 500, 500);
}

void GameUI::GamePlay::createEnamies9()
{
    enemies9.loadAnimation("black", 5, 1.25, 1.25);
    enemies9.setPosition("black", 550, 550);
}

void GameUI::GamePlay::createEnamiesBoss()
{
    enemiesBoss.loadAnimation("boss", 8, 1.25, 1.25);
    enemiesBoss.setPosition("boss", 200, 200);
}

void GameUI::GamePlay::drawBackground(sf::RenderWindow &window)
{
    window.draw(getBackgroundSprite());
}

void GameUI::GamePlay::drawTeamScore(sf::RenderWindow &window)
{
    window.draw(getTeamScoreSprite());
}

void GameUI::GamePlay::drawLifeBoard(sf::RenderWindow &window)
{
    window.draw(getLifeBoardSprite());
}

const sf::Sprite &GameUI::GamePlay::getTeamScoreSprite() const
{
    return TeamScoreImage.getSprite();
}

const sf::Sprite &GameUI::GamePlay::getBackgroundSprite() const
{
    return backgroundImage.getSprite();
}

const sf::Sprite &GameUI::GamePlay::getLifeBoardSprite() const
{
    return LifeBoardImage.getSprite();
}

void GameUI::GamePlay::centerImage(ImageManager &img, float windowWidth, float windowHeight)
{
    sf::Sprite &sprite = img.getSprite();
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}

void GameUI::GamePlay::shapebuilder(sf::RenderWindow &window)
{
}

void GameUI::GamePlay::loadFont(const std::string &fontPath)
{
    if (!font.loadFromFile(fontPath))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}

void GameUI::GamePlay::update()
{
}

void GameUI::GamePlay::render(sf::RenderWindow &window)
{
    window.clear();

    float windowWidth = window.getSize().x;
    float windowHeight = window.getSize().y;
    if (setBackground("assets/image/Background/background2.png", windowWidth, windowHeight))
    {
        drawBackground(window);
    }
    else
    {
        std::cerr << "Failed to set background" << std::endl;
    }

    if (setTeamScore("assets/image/Element/score.png", windowWidth, windowHeight))
    {
        drawTeamScore(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    if (setLifeBoard("assets/image/Element/life_board.png", windowWidth, windowHeight))
    {
        drawLifeBoard(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    player1.update("red");
    player1.render(window, "red");

    player2.update("blue");
    player2.render(window, "blue");

    enemies1.update("green");
    enemies1.render(window, "green");

    enemies2.update("yellow");
    enemies2.render(window, "yellow");

    enemies3.update("purple");
    enemies3.render(window, "purple");

    enemies4.update("orange");
    enemies4.render(window, "orange");

    enemies5.update("pink");
    enemies5.render(window, "pink");

    enemies6.update("cyan");
    enemies6.render(window, "cyan");

    enemies7.update("brown");
    enemies7.render(window, "brown");

    enemies8.update("white");
    enemies8.render(window, "white");

    enemies9.update("black");
    enemies9.render(window, "black");

    shapebuilder(window);
    window.display();
}

void GameUI::GamePlay::handleEvent(sf::Event &event)
{

    // move player using keyboard
    if (event.type == sf::Event::KeyPressed)
    {
        if (event.key.code == sf::Keyboard::Up)
        {
            player1.moveY("red", -5);
        }
        if (event.key.code == sf::Keyboard::Down)
        {
            player1.moveY("red", 5);
        }
        if (event.key.code == sf::Keyboard::Left)
        {
            player1.moveXRight("red", -5);
        }
        if (event.key.code == sf::Keyboard::Right)
        {
            player1.moveXRight("red", 5);
        }
    }


    if (event.type == sf::Event::MouseButtonPressed)
    {
        sf::Vector2f mousePos = sf::Vector2f(event.mouseButton.x, event.mouseButton.y);
        std::cout << "x: " << mousePos.x << " y: " << mousePos.y << std::endl;
    }
}
```


