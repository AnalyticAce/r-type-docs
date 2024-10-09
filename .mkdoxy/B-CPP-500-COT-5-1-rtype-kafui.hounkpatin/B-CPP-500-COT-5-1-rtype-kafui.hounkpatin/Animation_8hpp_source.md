

# File Animation.hpp

[**File List**](files.md) **>** [**Animation**](dir_d16831a22b1176c437f87c2d0440ff32.md) **>** [**Animation.hpp**](Animation_8hpp.md)

[Go to the documentation of this file](Animation_8hpp.md)


```C++
#ifndef ANIMATION_HPP
#define ANIMATION_HPP
#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>
#include <iostream>
#include <map>
#include <string>

struct AnimationData {
    sf::Sprite sprite;
    int totalFrames;
    int currentFrame;
    sf::Clock clock;
};

class Animation
{
private:
    sf::Sprite sprite;
    sf::Texture texture;
    std::map<std::string, sf::Texture> animations;
    float frameTime; 
    int currentFrame;
    //int totalFrames;
    //sf::Clock clock;
    std::map<std::string, AnimationData> animationsData;

public:
    Animation();
    ~Animation();

    void loadAnimation(const std::string& name_by_color, int frames); 
    void update(const std::string& name_by_color);
    void render(sf::RenderWindow& window, const std::string& name_by_color);
    void setScale(float scaleX, float scaleY);
    void setPosition(const std::string& name_by_color, float x, float y);
    void moveY(const std::string& name_by_color, float SpeedY);
    void moveYUp(const std::string& name_by_color, float SpeedY);
    void moveXRight(const std::string& name_by_color, float SpeedX);
    void moveXLeft(const std::string& name_by_color, float SpeedX);
    sf::Sprite& getSprite() { return sprite; } 
};

#endif
```


