

# File InputManager.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Input**](dir_cc001759347ed62121aae3ac8586610a.md) **>** [**InputManager.cpp**](InputManager_8cpp.md)

[Go to the documentation of this file](InputManager_8cpp.md)


```C++
#include "../../../include/Engine/Input/InputManager.hpp"

InputManager::InputManager()
{
    button.left = button.right = button.up = button.down = button.attack = button.escape = false;
}

InputManager::~InputManager()
{
}

InputManager::Button InputManager::getButton() const
{
    return button;
}

void InputManager::handleInput(sf::Event event, sf::RenderWindow &window)
{
    if (event.type == sf::Event::KeyPressed)
    {
        switch (event.key.code)
        {
        case sf::Keyboard::Escape:
            button.escape = true;
            break;

        case sf::Keyboard::Left:
            button.left = true;
            break;

        case sf::Keyboard::Right:
            button.right = true;
            break;

        case sf::Keyboard::Up:
            button.up = true;
            break;

        case sf::Keyboard::Down:
            button.down = true;
            break;
        case sf::Keyboard::A:
            button.attack = true;
            break;

        default:
            break;
        }
    }

    if (event.type == sf::Event::KeyReleased)
    {
        switch (event.key.code)
        {
        case sf::Keyboard::Escape:
            button.escape = false;
            break;

        case sf::Keyboard::Left:
            button.left = false;
            break;

        case sf::Keyboard::Right:
            button.right = false;
            break;

        case sf::Keyboard::Up:
            button.up = false;
            break;

        case sf::Keyboard::Down:
            button.down = false;
            break;
        case sf::Keyboard::A:
            button.attack = false;
            break;

        default:
            break;
        }
    }
}

void TextManager::drawText(const std::string &text, float x, float y, sf::Color color,
                           sf::RenderWindow &window)
{
    sf::Text sfText;
    sfText.setFont(font);
    sfText.setString(text);
    sfText.setPosition(x, y);
    sfText.setFillColor(color);
    window.draw(sfText);
}

void TextManager::drawTextTemporarily(const std::string &text, float x, float y, sf::Color color,
                                      float duration, sf::RenderWindow &window)
{

    TemporaryText tempText;
    tempText.text.setFont(font);
    tempText.text.setString(text);
    tempText.text.setPosition(x, y);
    tempText.text.setFillColor(color);
    tempText.duration = duration;
    tempText.clock.restart();
    tempTexts.push_back(tempText);
}

void TextManager::loadFont(const std::string &fontPath)
{
    if (!font.loadFromFile(fontPath))
    {
        std::cerr << "Failed to load font." << std::endl;
    }
}
```


