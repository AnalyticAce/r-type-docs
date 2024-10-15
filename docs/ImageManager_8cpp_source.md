

# File ImageManager.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Image**](dir_fe84c1fa4d9371df2d37e162ea73f06d.md) **>** [**ImageManager.cpp**](ImageManager_8cpp.md)

[Go to the documentation of this file](ImageManager_8cpp.md)


```C++
#include "../../../include/Engine/Image/ImageManager.hpp"

ImageManager::ImageManager()
{
}

ImageManager::~ImageManager()
{
    destroyImage();
}

bool ImageManager::createImage(const std::string &filePath)
{
    if (!texture.loadFromFile(filePath))
    {
        std::cerr << "Erreur: impossible de charger l'image depuis " << filePath << std::endl;
        return false;
    }
    sprite.setTexture(texture);
    return true;
}

void ImageManager::setPosition(float x, float y)
{
    sprite.setPosition(x, y);
}

void ImageManager::setScale(float scaleX, float scaleY)
{
    sprite.setScale(scaleX, scaleY);
}

void ImageManager::draw(sf::RenderWindow &window)
{
    window.draw(sprite);
}

void ImageManager::destroyImage()
{
}

sf::FloatRect ImageManager::getGlobalBounds()
{
    return sprite.getGlobalBounds();
}

void ImageManager::fitToScreen(float windowWidth, float windowHeight)
{
    if (texture.getSize().x == 0 || texture.getSize().y == 0)
    {
        return;
    }

    float scaleX = windowWidth / texture.getSize().x;
    float scaleY = windowHeight / texture.getSize().y;
    float scale = std::max(scaleX, scaleY);

    sprite.setScale(scale, scale);
    sf::FloatRect bounds = sprite.getLocalBounds();
    sprite.setOrigin(bounds.width / 2, bounds.height / 2);
    sprite.setPosition(windowWidth / 2, windowHeight / 2);
}
```


