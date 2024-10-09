

# File Setting.hpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Setting**](dir_956aa9544b32550cc8445cdad480e0fc.md) **>** [**Setting.hpp**](Setting_8hpp.md)

[Go to the documentation of this file](Setting_8hpp.md)


```C++
#ifndef SETTING_HPP
#define SETTING_HPP

#include <SFML/Graphics.hpp>
#include <iostream>
#include <string>
#include <memory>

#include "../../../include/Engine/Image/ImageManager.hpp"
#include "../../../include/Engine/Audio/AudioManager.hpp"
#include "../../../include/Engine/Mouse/MouseManager.hpp"

class Setting {
public:
    Setting();
    ~Setting();
    bool setsetting(const std::string &filePath, float windowWidth, float windowHeight);
    void drawsetting(sf::RenderWindow& window);
    bool setbackground(const std::string &filePath, float windowWidth, float windowHeight);
    void drawbackground(sf::RenderWindow& window);
    void getname();
    const sf::Sprite& getSettingSprite() const;
    const sf::Sprite& getBackgroundSprite() const;
    // get mouse object
    MouseManager& getMouse() { return mouse; }
private:
    ImageManager settingImage;
    ImageManager backgroundImage;
    AudioManager RoomMusic;
    MouseManager mouse;
    void centerImage(ImageManager& img, float windowWidth, float windowHeight);
};

class TextInputManager {
public:
private:

};



#endif
```


