

# File ImageManager.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Image**](dir_9d4cae504f03fb905f759f63b05c069d.md) **>** [**ImageManager.hpp**](ImageManager_8hpp.md)

[Go to the documentation of this file](ImageManager_8hpp.md)


```C++
#ifndef IMAGEMANAGER_HPP
#define IMAGEMANAGER_HPP

#include <SFML/Graphics.hpp>
#include <iostream>
#include <string>

class ImageManager {
public:
    ImageManager();

    ~ImageManager();

    bool createImage(const std::string &filePath);

    void setPosition(float x, float y);

    void setScale(float scaleX, float scaleY);

    void draw(sf::RenderWindow &window);

    void destroyImage();

    sf::FloatRect getGlobalBounds();
    sf::Texture texture;

    sf::Sprite& getSprite() { return sprite; }
    const sf::Sprite& getSprite() const { return sprite; }
    void fitToScreen(float windowWidth, float windowHeight);
private:
    sf::Sprite sprite;
};

#endif // IMAGEMANAGER_HPP
```


