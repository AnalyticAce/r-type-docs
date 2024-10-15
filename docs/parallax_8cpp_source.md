

# File parallax.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Parallax**](dir_19cd604a8f0e57207fc6eb0bc4ed780e.md) **>** [**parallax.cpp**](parallax_8cpp.md)

[Go to the documentation of this file](parallax_8cpp.md)


```C++
#include "../../../include/Engine/Parallax/parallax.hpp"

Parallax::Parallax(const std::string &file1, const std::string &file2, float speed1, float speed2)
{
    if (!texture1.loadFromFile(file1) || !texture2.loadFromFile(file2))
    {
        throw std::runtime_error("Impossible de charger les fichiers d'image.");
    }

    sprite1.setTexture(texture1);
    sprite2.setTexture(texture2);

    this->speed1 = speed1;
    this->speed2 = speed2;

    sprite1.setPosition(0.f, 0.f);
    sprite2.setPosition(1920.f, 0.f);
}

void Parallax::update(float deltaTime)
{
    sprite1.move(-speed1 * deltaTime, 0.f);
    sprite2.move(-speed2 * deltaTime, 0.f);

    if (sprite1.getPosition().x + texture1.getSize().x < 0)
    {
        std::cout << sprite1.getPosition().x + texture1.getSize().x << std::endl;
        sprite1.setPosition(1880.f, 0.f);
    }
    if (sprite2.getPosition().x + texture2.getSize().x < 0)
    {
        std::cout << sprite2.getPosition().x + texture2.getSize().x << std::endl;
        sprite2.setPosition(1880.f, 0.f);
    }
}

void Parallax::draw(sf::RenderWindow &window)
{
    window.draw(sprite2);
    window.draw(sprite1);
}
```


