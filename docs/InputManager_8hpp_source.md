

# File InputManager.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Input**](dir_011a5bb273ab46acf9be02ac4bf7f0a3.md) **>** [**InputManager.hpp**](InputManager_8hpp.md)

[Go to the documentation of this file](InputManager_8hpp.md)


```C++
#ifndef INPUTMANAGER_HPP
#define INPUTMANAGER_HPP

#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>
#include <iostream>

class InputManager
{
    struct Button
    {
        bool left;   
        bool right;  
        bool up;     
        bool down;   
        bool attack; 
        bool escape; 
    };

private:
    Button button;

public:
    InputManager();

    ~InputManager();

    void handleInput(sf::Event event, sf::RenderWindow &window);

    Button getButton(void) const;
};

struct TemporaryText
{
    sf::Text text;
    sf::Clock clock;
    float duration;
};

class TextManager
{
private:
    sf::Font font;
    sf::Event event;
    InputManager input;
    std::vector<TemporaryText> tempTexts;

public:
    TextManager() {};
    void drawText(const std::string &text, float x, float y, sf::Color color,
                  sf::RenderWindow &window);
    void loadFont(const std::string &fontPath);
    void render();
    void handleEvent();
    void drawTextTemporarily(const std::string &text, float x, float y, sf::Color color,
                             float duration, sf::RenderWindow &window);
    sf::RenderWindow &GetWindow();
};

#endif // INPUTMANAGER_HPP
```


