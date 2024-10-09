

# File Setting.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Setting**](dir_956aa9544b32550cc8445cdad480e0fc.md) **>** [**Setting.cpp**](Setting_8cpp.md)

[Go to the documentation of this file](Setting_8cpp.md)


```C++
#include "Setting.hpp"

Setting::Setting() 
{
    RoomMusic.playMusic("../../../assets/audio/Music/menu1.ogg");
}

Setting::~Setting() {}

bool Setting::setsetting(const std::string &filePath, float windowWidth, float windowHeight) {
    if (settingImage.createImage(filePath)) {
        settingImage.fitToScreen(windowWidth / 3.5, windowHeight / 3.5);
        centerImage(settingImage, windowWidth, windowHeight);
        return true;
    } else {
        std::cerr << "Failed to load setting image." << std::endl;
        return false;
    }
}

bool Setting::setbackground(const std::string &filePath, float windowWidth, float windowHeight) {
    if (backgroundImage.createImage(filePath)) {
        backgroundImage.fitToScreen(windowWidth, windowHeight);
        return true;
    } else {
        std::cerr << "Failed to load background image." << std::endl;
        return false;
    }
}

void Setting::drawbackground(sf::RenderWindow& window) {
    window.draw(getBackgroundSprite());
}

void Setting::drawsetting(sf::RenderWindow& window) {
    window.draw(getSettingSprite());
}

const sf::Sprite& Setting::getSettingSprite() const {
    return settingImage.getSprite();
}

const sf::Sprite& Setting::getBackgroundSprite() const {
    return backgroundImage.getSprite();
}

void Setting::centerImage(ImageManager& img, float windowWidth, float windowHeight) {
    sf::Sprite& sprite = img.getSprite();
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}

void Setting::getname() {
    
}
```


