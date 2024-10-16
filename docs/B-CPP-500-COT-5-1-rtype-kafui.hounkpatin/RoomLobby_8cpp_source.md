

# File RoomLobby.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**RoomLobby.cpp**](RoomLobby_8cpp.md)

[Go to the documentation of this file](RoomLobby_8cpp.md)


```C++
#include "RoomLobby.hpp"

GameUI::RoomLobby::RoomLobby(ScreenManager &screenManager)
    : screenManager(screenManager), activeInput(0)
{
    if (!font.loadFromFile("assets/font/Bangers.ttf"))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
    textfieldsetter(font);
}

void GameUI::RoomLobby::update()
{
}

void GameUI::RoomLobby::loadFont(const std::string &fontPath)
{
    if (!font.loadFromFile(fontPath))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}

bool GameUI::RoomLobby::setRoomLobby(const std::string &filePath, float windowWidth,
                                     float windowHeight)
{
    if (RoomLobbyImage.createImage(filePath))
    {
        RoomLobbyImage.fitToScreen(windowWidth / 3.5, windowHeight / 3.5);
        centerImage(RoomLobbyImage, windowWidth, windowHeight);
        return true;
    }
    else
    {
        std::cerr << "Failed to load RoomLobby image." << std::endl;
        return false;
    }
}

bool GameUI::RoomLobby::setBackground(const std::string &filePath, float windowWidth,
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

bool GameUI::RoomLobby::setBackButton(const std::string &filePath, float windowWidth,
                                      float windowHeight)
{
    if (backgroundImage.createImage(filePath))
    {
        backButtonImage.setPosition(10, 10);
        return true;
    }
    else
    {
        std::cerr << "Failed to load background image." << std::endl;
        return false;
    }
}

void GameUI::RoomLobby::drawBackground(sf::RenderWindow &window)
{
    window.draw(getBackgroundSprite());
}

void GameUI::RoomLobby::drawRoomLobby(sf::RenderWindow &window)
{
    window.draw(getRoomLobbySprite());
}

void GameUI::RoomLobby::drawBackButton(sf::RenderWindow &window)
{
    window.draw(getBackgroundSprite());
}

const sf::Sprite &GameUI::RoomLobby::getRoomLobbySprite() const
{
    return RoomLobbyImage.getSprite();
}

const sf::Sprite &GameUI::RoomLobby::getBackgroundSprite() const
{
    return backgroundImage.getSprite();
}

const sf::Sprite &GameUI::RoomLobby::getBackButtonSprite() const
{
    return backButtonImage.getSprite();
}

void GameUI::RoomLobby::centerImage(ImageManager &img, float windowWidth, float windowHeight)
{
    sf::Sprite &sprite = img.getSprite();
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}

void GameUI::RoomLobby::textfieldsetter(sf::Font &font)
{
    textip.setFont(font);
    textip.setCharacterSize(40);
    textip.setFillColor(sf::Color::Black);
    textip.setPosition(515.f, 150.f);

    textport.setFont(font);
    textport.setCharacterSize(40);
    textport.setFillColor(sf::Color::Black);
    textport.setPosition(515.f, 320.f);

    textname.setFont(font);
    textname.setCharacterSize(40);
    textname.setFillColor(sf::Color::Black);
    textname.setPosition(515.f, 490.f);
}

void GameUI::RoomLobby::shapebuilder(sf::RenderWindow &window)
{
    this->rect1 = shapeManager1.drawRectangle(window, 515, 150, 340, 35, sf::Color::Red, 5);
    sf::FloatRect textBounds = textip.getLocalBounds();
    textip.setOrigin(textBounds.left + textBounds.width / 2.0f,
                     textBounds.top + textBounds.height / 2.0f);
    textip.setPosition(rect1.getPosition().x + rect1.getSize().x / 2.0f,
                       rect1.getPosition().y + rect1.getSize().y / 2.0f);
    window.draw(textip);

    this->rect2 = shapeManager2.drawRectangle(window, 515, 320, 340, 35, sf::Color::Red, 5);
    sf::FloatRect textBounds2 = textport.getLocalBounds();
    textport.setOrigin(textBounds2.left + textBounds2.width / 2.0f,
                       textBounds2.top + textBounds2.height / 2.0f);
    textport.setPosition(rect2.getPosition().x + rect2.getSize().x / 2.0f,
                         rect2.getPosition().y + rect2.getSize().y / 2.0f);
    window.draw(textport);

    this->rect3 = shapeManager3.drawRectangle(window, 515, 490, 340, 35, sf::Color::Red, 5);
    sf::FloatRect textBounds3 = textname.getLocalBounds();
    textname.setOrigin(textBounds3.left + textBounds3.width / 2.0f,
                       textBounds3.top + textBounds3.height / 2.0f);
    textname.setPosition(rect3.getPosition().x + rect3.getSize().x / 2.0f,
                         rect3.getPosition().y + rect3.getSize().y / 2.0f);
    window.draw(textname);

    this->rect4 = shapeManager4.drawRectangle(window, 550, 590, 230, 35, sf::Color::Red, 5);
    sf::FloatRect textBounds4 = textname.getLocalBounds();
    textname.setOrigin(textBounds4.left + textBounds4.width / 2.0f,
                       textBounds4.top + textBounds4.height / 2.0f);
    textname.setPosition(rect4.getPosition().x + rect4.getSize().x / 2.0f,
                         rect4.getPosition().y + rect4.getSize().y / 2.0f);
}

void GameUI::RoomLobby::render(sf::RenderWindow &window)
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

    if (setRoomLobby("assets/image/Element/panel.png", windowWidth, windowHeight))
    {
        drawRoomLobby(window);
    }
    else
    {
        std::cerr << "Failed to set setting" << std::endl;
    }

    shapebuilder(window);
    window.display();
}

void GameUI::RoomLobby::handleEvent(sf::Event &event)
{
    if (event.type == sf::Event::TextEntered)

    {
        if (event.text.unicode < 128)
        {
            if (event.text.unicode == '\b')
            {
                if (!inputIp.empty() && activeInput == 0)
                {
                    inputIp.pop_back();
                    getTextIp().setString(inputIp);
                }
                else if (!inputPort.empty() && activeInput == 1)
                {
                    inputPort.pop_back();
                    getTextPort().setString(inputPort);
                }
                else if (!inputName.empty() && activeInput == 2)
                {
                    inputName.pop_back();
                    getTextName().setString(inputName);
                }
            }
            else if (event.text.unicode == '\t')
            {
                activeInput = (activeInput + 1) % 3;
            }
            else
            {
                if (activeInput == 0)
                {
                    inputIp += static_cast<char>(event.text.unicode);
                    getTextIp().setString(inputIp);
                }
                else if (activeInput == 1)
                {
                    inputPort += static_cast<char>(event.text.unicode);
                    getTextPort().setString(inputPort);
                }
                else if (activeInput == 2)
                {
                    inputName += static_cast<char>(event.text.unicode);
                    getTextName().setString(inputName);
                }
            }
        }
    }

    if (event.type == sf::Event::MouseButtonPressed)
    {
        sf::Vector2i mousePos = sf::Vector2i(event.mouseButton.x, event.mouseButton.y);
        if (getRect1().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        {
            activeInput = 0;
        }
        else if (getRect2().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        {
            activeInput = 1;
        }
        else if (getRect3().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        {
            activeInput = 2;
        }
        else if (getRect4().getGlobalBounds().contains(static_cast<sf::Vector2f>(mousePos)))
        {
            std::cout << "Button clicked" << std::endl;
            getButtonSound().playSound("assets/audio/Effect/button.mp3");
            screenManager.switchToScreen("GameLobby");
            std::cout << inputIp << std::endl;
            std::cout << inputPort << std::endl;
            std::cout << inputName << std::endl;
            // std::string server_ip = "127.0.0.1";
            protocol::PlayerAction player_action = {1, 1, {0x04, 0x02}};
            std::thread udp_thread(&Client::send_udp_message, &screenManager.client,
                                   std::ref(player_action), inputIp, std::stoi(inputPort),
                                   std::ref(inputName));
            udp_thread.join();
            event.type = sf::Event::Closed;
        }
    }
}
```


