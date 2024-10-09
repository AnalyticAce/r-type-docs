

# File Animation.cpp

[**File List**](files.md) **>** [**Animation**](dir_306a0e6e66590168765549196d987f73.md) **>** [**Animation.cpp**](Animation_8cpp.md)

[Go to the documentation of this file](Animation_8cpp.md)


```C++
#include "../../../include/Engine/Animation/Animation.hpp"

Animation::Animation() : frameTime(0.1f), currentFrame(0)/*, totalFrames(16)*/
{
    animations["red"].loadFromFile("../../../assets/image/Player/red1.gif");
    animations["gray"].loadFromFile("../../../assets/image/Player/gray.png");
    sprite.setScale(2.0f, 2.0f);
}

Animation::~Animation() {}

void Animation::loadAnimation(const std::string& name_by_color, int frames)
{
    if (animations.find(name_by_color) != animations.end()) {
        AnimationData data;
        data.sprite.setTexture(animations[name_by_color]);
        data.totalFrames = frames;
        data.currentFrame = 0;
        data.sprite.setScale(2.0f, 2.0f);  // Tu peux définir une échelle personnalisée ici
        animationsData[name_by_color] = data;
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
    /*if (animations.find(name_by_color) != animations.end()) {
        texture = animations[name_by_color];
        sprite.setTexture(texture);
        currentFrame = 0;
        totalFrames = frames;
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }*/
}

void Animation::update(const std::string& name_by_color)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        AnimationData& data = animationsData[name_by_color];
        int frameWidth = data.sprite.getTexture()->getSize().x / data.totalFrames;

        if (data.clock.getElapsedTime().asSeconds() >= frameTime) {
            data.currentFrame = (data.currentFrame + 1) % data.totalFrames;
            data.sprite.setTextureRect(sf::IntRect(data.currentFrame * frameWidth, 0, frameWidth, data.sprite.getTexture()->getSize().y));
            data.clock.restart();
        }
    }
    /*if (animationsData.find(name_by_color) != animationsData.end()) {
        AnimationData& data = animationsData[name_by_color];
        int frameWidth = data.sprite.getTexture()->getSize().x / data.totalFrames;

        if (clock.getElapsedTime().asSeconds() >= frameTime) {
            data.currentFrame = (data.currentFrame + 1) % data.totalFrames;
            data.sprite.setTextureRect(sf::IntRect(data.currentFrame * frameWidth, 0, frameWidth, data.sprite.getTexture()->getSize().y));
            clock.restart();
        }
    }*/
    /*int frameWidth = texture.getSize().x / totalFrames;

    if (clock.getElapsedTime().asSeconds() >= frameTime) {
        currentFrame = (currentFrame + 1) % totalFrames;
        sprite.setTextureRect(sf::IntRect(currentFrame * frameWidth, 0, frameWidth, texture.getSize().y));
        clock.restart();
    }*/
}

void Animation::render(sf::RenderWindow& window, const std::string& name_by_color)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        window.draw(animationsData[name_by_color].sprite);
    }
    /*window.draw(sprite);*/
}

void Animation::setScale(float scaleX, float scaleY)
{
    sprite.setScale(scaleX, scaleY);
}

void Animation::setPosition(const std::string& name_by_color, float x, float y)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        animationsData[name_by_color].sprite.setPosition(x, y);
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveY(const std::string& name_by_color, float SpeedY)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();

        animationsData[name_by_color].sprite.setPosition(currentPosition.x, currentPosition.y + SpeedY);
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveYUp(const std::string& name_by_color, float SpeedY)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();
        animationsData[name_by_color].sprite.setPosition(currentPosition.x, currentPosition.y - SpeedY);
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveXRight(const std::string& name_by_color, float SpeedX)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();
        animationsData[name_by_color].sprite.setPosition(currentPosition.x + SpeedX, currentPosition.y);
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveXLeft(const std::string& name_by_color, float SpeedX)
{
    if (animationsData.find(name_by_color) != animationsData.end()) {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();
        animationsData[name_by_color].sprite.setPosition(currentPosition.x - SpeedX, currentPosition.y);
    } else {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}
```


