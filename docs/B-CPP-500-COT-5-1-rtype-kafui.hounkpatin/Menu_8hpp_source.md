

# File Menu.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Save**](dir_7f2caee7a039a4df72b6a79e2fa54694.md) **>** [**Menu.hpp**](Menu_8hpp.md)

[Go to the documentation of this file](Menu_8hpp.md)


```C++
#ifndef MENU_HPP
#define MENU_HPP
#include <SFML/Audio.hpp>
#include <SFML/Graphics.hpp>
#include <iostream>

#include "../../include/Engine/Animation/Animation.hpp"
#include "../../include/Engine/Audio/AudioManager.hpp"
#include "../../include/Engine/Image/ImageManager.hpp"
#include "../../include/Engine/Input/InputManager.hpp"
#include "../../include/Engine/Mouse/MouseManager.hpp"
#include "../../include/Engine/Shape/ShapeManager.hpp"
#include "MenuWindowManager.hpp"

#define BASE_WIDTH 1920
#define BASE_HEIGHT 1080

class Menu
{
public:
    Menu();
    void run();

    sf::RectangleShape &getRect1() { return rect1; }
    sf::RectangleShape &getRect2() { return rect2; }

    // const sf::Sprite& getBackgroundSprite() const;
    const sf::Sprite &getBackgroundSprite() const { return backgroundImage.getSprite(); }
    const sf::Sprite &getPlayButtonSprite() const;
    void drawGameLobby(sf::RenderWindow &window);

    const sf::Sprite &getGameLobbySprite() const { return GameLobbyImage.getSprite(); }

    bool setBackground(const std::string &filePath, float windowWidth, float windowHeight)
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

    void drawBackground(sf::RenderWindow &window) { window.draw(getBackgroundSprite()); }

private:
    void handleEvents();
    void update();
    void render();
    void openSettings();
    void applyChanges();
    void initializeMusic();
    void loadImages();
    void drawMainMenu();
    void renderSettings();
    void handleNavigationClicks(float mouseX, float mouseY);
    void loadAndSetupImage(ImageManager &img, const std::string &path, float scaleX, float scaleY,
                           float posX, float posY);
    void handleButtonClicks(float mouseX, float mouseY);
    void handleWindowEvents(const sf::Event &event);
    void handleMouseEvents(const sf::Event &event);
    void handleSettingsClicks(const sf::Event &event);
    void handleVolumeClicks(float mouseX, float mouseY);
    void decreaseVolume();
    void increaseVolume();
    void decreaseResolution();
    void increaseResolution();
    void drawSettingsBackground();
    void drawSettingsElements();
    void drawSoundToggle();
    void updateElementPositions(const sf::Vector2u &windowSize);
    void updateElementPosition(ImageManager &img, float x, float y, float scaleX, float scaleY);
    bool handleSettingsEvents();
    void handleSoundToggleClicks(float mouseX, float mouseY);
    void handleResolutionClicks(float mouseX, float mouseY);
    void loadVolumeImages();
    void updateVolumeImage();
    void loadResolutionImages();
    void updateResolutionImage();

    void centerImage(ImageManager &img, float windowWidth, float windowHeight);

    WindowManager windowManager;
    AudioManager audioManager;

    sf::RectangleShape rect1, rect2;

    ImageManager GameLobbyImage, backgroundImage, startButtonImage, settingsButtonImage;
    ImageManager setVolumeImage, soundImage, screenResolutionImage, goBackButtonImage;
    ImageManager applyChangesButtonImage, plusButton, moinsButton, onImage;
    ImageManager offImage, infButton, supButton, screen_infButton, screen_supButton;
    ImageManager asteroid_1, asteroid_2, asteroid_3, asteroid_4;

    InputManager inputManager;
    MouseManager mouseManager;

    sf::RenderWindow &window;
    bool settingsOpen = true;
    bool isSoundOn;
    int volumeLevel;
    sf::Music music;

    std::vector<sf::Texture> volumeTextures;
    std::vector<sf::Texture> resolutionTextures;
    sf::Sprite resolutionSprite;
    sf::Sprite volumeSprite;

    std::vector<sf::Vector2u> resolutions = {{1920, 1080}};
    int currentResolutionIndex;
};

#endif
```


