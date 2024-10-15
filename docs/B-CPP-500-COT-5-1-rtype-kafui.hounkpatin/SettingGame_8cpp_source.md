

# File SettingGame.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Save**](dir_7f2caee7a039a4df72b6a79e2fa54694.md) **>** [**SettingGame.cpp**](SettingGame_8cpp.md)

[Go to the documentation of this file](SettingGame_8cpp.md)


```C++
#include "Menu.hpp"

void Menu::loadVolumeImages()
{
    for (int i = 10; i <= 100; i += 10)
    {
        sf::Texture texture;
        if (texture.loadFromFile("assets/image/Element/Volume/" + std::to_string(i) + ".png"))
        {
            volumeTextures.push_back(texture);
        }
        else
        {
            std::cerr << "Error loading volume image for " << i << std::endl;
        }
    }
}

void Menu::loadResolutionImages()
{
    std::vector<sf::Vector2u> availableResolutions = {{BASE_WIDTH, BASE_HEIGHT}};

    for (const auto &res : availableResolutions)
    {
        sf::Texture texture;
        std::string resolutionStr = std::to_string(res.x) + "_" + std::to_string(res.y);
        if (texture.loadFromFile("assets/image/Element/Screen/" + resolutionStr + ".png"))
        {
            resolutionTextures.push_back(texture);
        }
        else
        {
            std::cerr << "Error: Unable to load resolution image " << resolutionStr << std::endl;
        }
    }
}

void Menu::updateResolutionImage()
{
    if (currentResolutionIndex >= 0 && currentResolutionIndex < resolutionTextures.size())
    {
        resolutionSprite.setTexture(resolutionTextures[currentResolutionIndex]);
        resolutionSprite.setPosition(1200, 650);
        resolutionSprite.setScale(1.0f, 1.0f);
    }
}

void Menu::updateVolumeImage()
{
    int index = volumeLevel / 10 - 1;
    if (index >= 0 && index < volumeTextures.size())
    {
        volumeSprite.setTexture(volumeTextures[index]);
        volumeSprite.setPosition(1320, 250);
        volumeSprite.setScale(1.0f, 1.0f);
    }
}

void Menu::openSettings()
{
    bool settingsOpen = true;
    while (settingsOpen && window.isOpen())
    {
        settingsOpen = handleSettingsEvents();
        renderSettings();
    }
}

bool Menu::handleSettingsEvents()
{
    sf::Event event;
    while (window.pollEvent(event))
    {
        if (event.type == sf::Event::Closed)
        {
            window.close();
            return false;
        }
        if (event.type == sf::Event::KeyPressed && event.key.code == sf::Keyboard::Escape)
        {
            return false;
        }
        if (event.type == sf::Event::MouseButtonPressed &&
            event.mouseButton.button == sf::Mouse::Left)
        {
            handleSettingsClicks(event);
        }
    }
    return true;
}

void Menu::handleSettingsClicks(const sf::Event &event)
{
    float mouseX = static_cast<float>(event.mouseButton.x);
    float mouseY = static_cast<float>(event.mouseButton.y);

    handleVolumeClicks(mouseX, mouseY);
    handleSoundToggleClicks(mouseX, mouseY);
    handleResolutionClicks(mouseX, mouseY);
    handleNavigationClicks(mouseX, mouseY);
}

void Menu::handleVolumeClicks(float mouseX, float mouseY)
{
    if (moinsButton.getGlobalBounds().contains(mouseX, mouseY))
    {
        decreaseVolume();
    }
    if (plusButton.getGlobalBounds().contains(mouseX, mouseY))
    {
        increaseVolume();
    }
}

void Menu::decreaseVolume()
{
    if (volumeLevel > 0)
    {
        volumeLevel -= 10;
        music.setVolume(volumeLevel);
        updateVolumeImage();
    }
}

void Menu::increaseVolume()
{
    if (volumeLevel < 100)
    {
        volumeLevel += 10;
        music.setVolume(volumeLevel);
        updateVolumeImage();
    }
}

void Menu::handleSoundToggleClicks(float mouseX, float mouseY)
{
    if (infButton.getGlobalBounds().contains(mouseX, mouseY))
    {
        isSoundOn = false;
        music.pause();
    }
    if (supButton.getGlobalBounds().contains(mouseX, mouseY))
    {
        isSoundOn = true;
        music.play();
    }
}

void Menu::handleResolutionClicks(float mouseX, float mouseY)
{
    if (screen_infButton.getGlobalBounds().contains(mouseX, mouseY))
    {
        decreaseResolution();
    }
    if (screen_supButton.getGlobalBounds().contains(mouseX, mouseY))
    {
        increaseResolution();
    }
}

void Menu::decreaseResolution()
{
    if (currentResolutionIndex > 0)
    {
        currentResolutionIndex--;
        updateResolutionImage();
    }
}

void Menu::increaseResolution()
{
    if (currentResolutionIndex < resolutions.size() - 1)
    {
        currentResolutionIndex++;
        updateResolutionImage();
    }
}

void Menu::handleNavigationClicks(float mouseX, float mouseY)
{
    if (goBackButtonImage.getGlobalBounds().contains(mouseX, mouseY))
    {
        std::cout << "Go back button clicked" << std::endl;
        settingsOpen = false;
    }
    if (applyChangesButtonImage.getGlobalBounds().contains(mouseX, mouseY))
    {
        std::cout << "Apply changes button clicked" << std::endl;
        applyChanges();
    }
}

void Menu::renderSettings()
{
    window.clear(sf::Color::Black);
    drawSettingsBackground();
    drawSettingsElements();
    window.display();
}

void Menu::drawSettingsBackground()
{
    backgroundImage.draw(window);
}

void Menu::drawSettingsElements()
{
    setVolumeImage.draw(window);
    soundImage.draw(window);
    screenResolutionImage.draw(window);
    goBackButtonImage.draw(window);
    applyChangesButtonImage.draw(window);
    plusButton.draw(window);
    moinsButton.draw(window);
    window.draw(volumeSprite);
    drawSoundToggle();
    infButton.draw(window);
    supButton.draw(window);
    screen_infButton.draw(window);
    screen_supButton.draw(window);
    window.draw(resolutionSprite);
}

void Menu::drawSoundToggle()
{
    if (isSoundOn)
    {
        onImage.draw(window);
    }
    else
    {
        offImage.draw(window);
    }
}

void Menu::applyChanges()
{
    sf::Vector2u selectedResolution = resolutions[currentResolutionIndex];
    window.create(sf::VideoMode(selectedResolution.x, selectedResolution.y), "Game Menu");
    updateElementPositions(selectedResolution);
}

void Menu::updateElementPositions(const sf::Vector2u &newResolution)
{
    float scaleX = static_cast<float>(newResolution.x) / BASE_WIDTH;
    float scaleY = static_cast<float>(newResolution.y) / BASE_HEIGHT;

    // updateElementPosition(backgroundImage, 0, 0, scaleX, scaleY);
    // centerImage(titleImage, newResolution.x, newResolution.y);
    // updateElementPosition(titleImage, 700, 200, 1.5f * scaleX, 1.5f * scaleY);
    // updateElementPosition(startButtonImage, 860, 600, scaleX, scaleY);
    // updateElementPosition(settingsButtonImage, 860, 770, scaleX, scaleY);

    updateElementPosition(goBackButtonImage, 100, 900, scaleX, scaleY);
    updateElementPosition(applyChangesButtonImage, 1320, 900, scaleX, scaleY);
    updateElementPosition(setVolumeImage, 250, 250, scaleX, scaleY);
    updateElementPosition(moinsButton, 900, 200, scaleX, scaleY);
    updateElementPosition(plusButton, 1700, 250, scaleX, scaleY);
    updateElementPosition(soundImage, 250, 450, scaleX, scaleY);
    updateElementPosition(onImage, 1300, 450, scaleX, scaleY);
    updateElementPosition(offImage, 1300, 450, scaleX, scaleY);
    updateElementPosition(infButton, 900, 450, scaleX, scaleY);
    updateElementPosition(supButton, 1700, 450, scaleX, scaleY);
    updateElementPosition(screenResolutionImage, 250, 650, scaleX, scaleY);
    updateElementPosition(screen_infButton, 900, 650, scaleX, scaleY);
    updateElementPosition(screen_supButton, 1700, 650, scaleX, scaleY);
}

void Menu::updateElementPosition(ImageManager &element, float x, float y, float scaleX,
                                 float scaleY)
{
    element.setPosition(x * scaleX, y * scaleY);
    element.setScale(scaleX, scaleY);
}
```


