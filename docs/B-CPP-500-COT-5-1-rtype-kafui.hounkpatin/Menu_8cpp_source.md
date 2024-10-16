

# File Menu.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Save**](dir_7f2caee7a039a4df72b6a79e2fa54694.md) **>** [**Menu.cpp**](Menu_8cpp.md)

[Go to the documentation of this file](Menu_8cpp.md)


```C++
#include "Menu.hpp"

Menu::Menu()
    : windowManager(BASE_WIDTH, BASE_HEIGHT, "Game Menu"), window(windowManager.GetWindow()),
      volumeLevel(100), isSoundOn(true), currentResolutionIndex(1)
{
    initializeMusic();
    loadImages();
    loadVolumeImages();
    updateVolumeImage();
    loadResolutionImages();
    updateResolutionImage();
}

void Menu::initializeMusic()
{
    if (!music.openFromFile("assets/audio/Music/UNSquadron.ogg"))
    {
        std::cerr << "Error: Unable to load music" << std::endl;
    }
    else
    {
        music.setLoop(true);
        music.play();
        music.setVolume(volumeLevel);
    }
}

// void Menu::centerImage(ImageManager& img, float windowWidth, float
// windowHeight) {
//     sf::Sprite& sprite = img.getSprite();
//     sf::FloatRect bounds = sprite.getLocalBounds();
//     sprite.setOrigin(bounds.width / 2, bounds.height / 2);
//     sprite.setPosition(windowWidth / 2, windowHeight / 2);
// }

void Menu::drawGameLobby(sf::RenderWindow &window)
{
    window.draw(getGameLobbySprite());
}

void Menu::loadImages()
{
    // loadAndSetupImage(backgroundImage,
    // "assets/image/Background/seamful_background.png", 1.5f, 1.5f, 0, 0);
    // loadAndSetupImage(titleImage, "assets/image/Button/logo.png", 1.5f, 1.5f,
    // 700, 200); loadAndSetupImage(startButtonImage,
    // "assets/image/Element/play.png", 1.0f, 1.0f, 860, 600);
    // loadAndSetupImage(settingsButtonImage,
    // "assets/image/Element/settings.png", 1.0f, 1.0f, 860, 770);
    loadAndSetupImage(setVolumeImage, "assets/image/Element/volume.png", 1.0f, 1.0f, 250, 250);
    loadAndSetupImage(moinsButton, "assets/image/Element/-.png", 1.0f, 1.0f, 900, 200);
    loadAndSetupImage(plusButton, "assets/image/Element/+.png", 1.0f, 1.0f, 1700, 250);
    loadAndSetupImage(soundImage, "assets/image/Element/sound.png", 1.0f, 1.0f, 250, 450);
    loadAndSetupImage(onImage, "assets/image/Element/on.png", 1.0f, 1.0f, 1300, 450);
    loadAndSetupImage(offImage, "assets/image/Element/off.png", 1.0f, 1.0f, 1300, 450);
    loadAndSetupImage(infButton, "assets/image/Element/inf.png", 1.0f, 1.0f, 900, 450);
    loadAndSetupImage(supButton, "assets/image/Element/sup.png", 1.0f, 1.0f, 1700, 450);
    loadAndSetupImage(screenResolutionImage, "assets/image/Element/resolution.png", 1.0f, 1.0f, 250,
                      650);
    loadAndSetupImage(screen_infButton, "assets/image/Element/inf.png", 1.0f, 1.0f, 900, 650);
    loadAndSetupImage(screen_supButton, "assets/image/Element/sup.png", 1.0f, 1.0f, 1700, 650);
    loadAndSetupImage(goBackButtonImage, "assets/image/Element/back.png", 1.0f, 1.0f, 100, 900);
    loadAndSetupImage(applyChangesButtonImage, "assets/image/Element/apply.png", 1.0f, 1.0f, 1320,
                      900);
}

void Menu::loadAndSetupImage(ImageManager &img, const std::string &path, float scaleX, float scaleY,
                             float posX, float posY)
{
    img.createImage(path);
    img.setScale(scaleX, scaleY);
    img.setPosition(posX, posY);
}

// void Menu::handleEvents() {
//     sf::Event event;
//     while (window.pollEvent(event)) {
//         handleWindowEvents(event);
//         handleMouseEvents(event);
//     }
// }

void Menu::handleWindowEvents(const sf::Event &event)
{
    if (event.type == sf::Event::Closed)
    {
        window.close();
    }
    // inputManager.handleInput(event, window);
    // mouseManager.handleMousePosition(window);
    // if (inputManager.getButton().escape) {
    //     window.close();
    // }
}

void Menu::handleMouseEvents(const sf::Event &event)
{
    if (event.type == sf::Event::MouseButtonPressed)
    {
        float mouseX = mouseManager.getMouseX();
        float mouseY = mouseManager.getMouseY();
        handleButtonClicks(mouseX, mouseY);
    }
}

void Menu::handleButtonClicks(float mouseX, float mouseY)
{
    if (startButtonImage.getGlobalBounds().contains(mouseX, mouseY))
    {
        std::cout << "Start button clicked" << std::endl;
    }
    if (settingsButtonImage.getGlobalBounds().contains(mouseX, mouseY))
    {
        std::cout << "Settings button clicked" << std::endl;
        openSettings();
    }
}

void Menu::update()
{
}

void Menu::render()
{
    window.clear(sf::Color::Black);

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
    window.display();
}

// void Menu::drawMainMenu() {
//     // backgroundImage.draw(window);
//     // titleImage.draw(window);
//     // startButtonImage.draw(window);
//     // settingsButtonImage.draw(window);
// }

void Menu::centerImage(ImageManager &img, float windowWidth, float windowHeight)
{
    sf::Sprite &sprite = img.getSprite();
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}

void Menu::run()
{
    while (window.isOpen())
    {
        // handleEvents();
        // update();
        render();
    }
}

int main()
{
    Menu menu;
    menu.run();
    return 0;
}
```


