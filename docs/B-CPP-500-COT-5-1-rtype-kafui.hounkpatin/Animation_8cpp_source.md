

# File Animation.cpp

[**File List**](files.md) **>** [**Animation**](dir_306a0e6e66590168765549196d987f73.md) **>** [**Animation.cpp**](Animation_8cpp.md)

[Go to the documentation of this file](Animation_8cpp.md)


```C++
#include "../../../include/Engine/Animation/Animation.hpp"

Animation::Animation() : frameTime(0.1f), currentFrame(0)
{
    animations["red"].loadFromFile("assets/image/Player/red1.gif");
    animations["green"].loadFromFile("assets/image/Enemie/Blaster.png");
    animations["yellow"].loadFromFile("assets/image/Enemie/BlasterB.png");
    animations["purple"].loadFromFile("assets/image/Enemie/BlasterC.png");
    animations["orange"].loadFromFile("assets/image/Enemie/SniperA.png");
    animations["pink"].loadFromFile("assets/image/Enemie/SniperB.png");
    animations["cyan"].loadFromFile("assets/image/Enemie/SniperC.png");
    animations["brown"].loadFromFile("assets/image/Enemie/TankerA.png");
    animations["white"].loadFromFile("assets/image/Enemie/TankerB.png");
    animations["black"].loadFromFile("assets/image/Enemie/TankerC.png");
    animations["boss"].loadFromFile("assets/image/Enemie/TankerC.png");
    animations["blue"].loadFromFile("assets/image/Player/blue.png");
}

Animation::~Animation()
{
}

void Animation::loadAnimation(const std::string &name_by_color, int frames, float x = 1, float y = 1)
{
    if (animations.find(name_by_color) != animations.end())
    {
        AnimationData data;
        data.sprite.setTexture(animations[name_by_color]);
        data.totalFrames = frames;
        data.currentFrame = 0;
        data.sprite.setScale(x, y);
        animationsData[name_by_color] = data;
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::update(const std::string &name_by_color)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        AnimationData &data = animationsData[name_by_color];
        int frameWidth = data.sprite.getTexture()->getSize().x / data.totalFrames;

        if (data.clock.getElapsedTime().asSeconds() >= frameTime)
        {
            data.currentFrame = (data.currentFrame + 1) % data.totalFrames;
            data.sprite.setTextureRect(sf::IntRect(data.currentFrame * frameWidth, 0, frameWidth,
                                                   data.sprite.getTexture()->getSize().y));
            data.clock.restart();
        }
    }
}

void Animation::render(sf::RenderWindow &window, const std::string &name_by_color)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        window.draw(animationsData[name_by_color].sprite);
    }
    /*window.draw(sprite);*/
}

void Animation::setScale(float scaleX, float scaleY)
{
    sprite.setScale(scaleX, scaleY);
}

void Animation::setPosition(const std::string &name_by_color, float x, float y)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        animationsData[name_by_color].sprite.setPosition(x, y);
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveY(const std::string &name_by_color, float SpeedY)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();

        animationsData[name_by_color].sprite.setPosition(currentPosition.x,
                                                         currentPosition.y + SpeedY);
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveYUp(const std::string &name_by_color, float SpeedY)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();
        animationsData[name_by_color].sprite.setPosition(currentPosition.x,
                                                         currentPosition.y - SpeedY);
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveXRight(const std::string &name_by_color, float SpeedX)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();
        animationsData[name_by_color].sprite.setPosition(currentPosition.x + SpeedX,
                                                         currentPosition.y);
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

void Animation::moveXLeft(const std::string &name_by_color, float SpeedX)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        sf::Vector2f currentPosition = animationsData[name_by_color].sprite.getPosition();
        animationsData[name_by_color].sprite.setPosition(currentPosition.x - SpeedX,
                                                         currentPosition.y);
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
    }
}

sf::Vector2f Animation::getPosition(const std::string &name_by_color)
{
    if (animationsData.find(name_by_color) != animationsData.end())
    {
        return animationsData[name_by_color].sprite.getPosition();
    }
    else
    {
        std::cerr << "Error: animation of " << name_by_color << " not found" << std::endl;
        return sf::Vector2f(0, 0);
    }
}
```


