

# File RoomLobby.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**RoomLobby.hpp**](RoomLobby_8hpp.md)

[Go to the documentation of this file](RoomLobby_8hpp.md)


```C++
#pragma once

#include "../../include/Engine/Audio/AudioManager.hpp"
#include "../../include/Engine/Image/ImageManager.hpp"
#include "../../include/Engine/Mouse/MouseManager.hpp"
#include "../../include/Engine/Shape/ShapeManager.hpp"
#include "GameLobby.hpp"
#include "ScreenManager.hpp"
#include <boost/asio.hpp>
#include <boost/asio/ip/udp.hpp>
#include <thread>

using boost::asio::ip::udp;
namespace GameUI
{
    class RoomLobby : public IScreen
    {
    private:
        sf::Font font;
        std::string input;
        int activeInput;
        ScreenManager &screenManager;
        ImageManager RoomLobbyImage, backgroundImage, backButtonImage;
        AudioManager ButtonSound;
        MouseManager mouse;
        sf::RectangleShape rect1, rect2, rect3, rect4;
        ShapeManager shapeManager1, shapeManager2, shapeManager3, shapeManager4;
        // Client client;
        void centerImage(ImageManager &img, float windowWidth, float windowHeight);

    public:
        std::string inputIp;
        std::string inputPort;
        std::string inputName;
        sf::Text textip, textport, textname;
        RoomLobby(ScreenManager &screenManager);
        void render(sf::RenderWindow &window) override;
        void loadFont(const std::string &fontPath);
        void handleEvent(sf::Event &event) override;
        void update() override;

        bool setBackButton(const std::string &filePath, float windowWidth, float windowHeight);
        bool setBackground(const std::string &filePath, float windowWidth, float windowHeight);
        bool setRoomLobby(const std::string &filePath, float windowWidth, float windowHeight);

        void drawRoomLobby(sf::RenderWindow &window);
        void drawBackground(sf::RenderWindow &window);
        void drawBackButton(sf::RenderWindow &window);

        const sf::Sprite &getRoomLobbySprite() const;
        const sf::Sprite &getBackgroundSprite() const;
        const sf::Sprite &getBackButtonSprite() const;

        void textfieldsetter(sf::Font &font);
        void shapebuilder(sf::RenderWindow &window);

        sf::Text &getTextIp() { return textip; }
        sf::Text &getTextPort() { return textport; }
        sf::Text &getTextName() { return textname; }

        sf::RectangleShape &getRect1() { return rect1; }
        sf::RectangleShape &getRect2() { return rect2; }
        sf::RectangleShape &getRect3() { return rect3; }
        sf::RectangleShape &getRect4() { return rect4; }

        AudioManager &getButtonSound() { return ButtonSound; }
        MouseManager &getMouse() { return mouse; }
    };
} // namespace GameUI
```


