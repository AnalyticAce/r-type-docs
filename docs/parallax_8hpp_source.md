

# File parallax.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Parallax**](dir_127bf1d17e553df95a92f785db2d2430.md) **>** [**parallax.hpp**](parallax_8hpp.md)

[Go to the documentation of this file](parallax_8hpp.md)


```C++
#include <SFML/Graphics.hpp>
#include <iostream>

class Parallax
{
public:
    Parallax(const std::string &file1, const std::string &file2, float speed1, float speed2);
    void update(float deltaTime);
    void draw(sf::RenderWindow &window);

private:
    sf::Texture texture1, texture2;
    sf::Sprite sprite1, sprite2;
    float speed1, speed2;
};
```


