

# File Window.cpp

[**File List**](files.md) **>** [**Client**](dir_133b3cdd880ca9e91a51b18f00995eeb.md) **>** [**Setting**](dir_956aa9544b32550cc8445cdad480e0fc.md) **>** [**Window.cpp**](Window_8cpp.md)

[Go to the documentation of this file](Window_8cpp.md)


```C++
#include "../../../include/Engine/Window/WindowManager.hpp"
#include "../../../include/Engine/Shape/ShapeManager.hpp"

WindowManager::WindowManager(int width, int height,
                            const std::string &windowName)
    : window(sf::VideoMode(width, height), windowName)

{
}

void WindowManager::keepOpen() {
    sf::Clock clock;
    while (window.isOpen()) {
        handleEvent();
        render();
    }
}

void WindowManager::loadFont(const std::string &fontPath) {
    if (!font.loadFromFile(fontPath)) {
    }
}


void WindowManager::render()
{
    window.clear();

    float windowWidth = window.getSize().x;
    float windowHeight = window.getSize().y;
    if (settings.setbackground("../../../assets/image/Background/background1.png", windowWidth, windowHeight)) {
        settings.drawbackground(window);
    } else {
        std::cerr << "Failed to set background" << std::endl;
    }

    if (settings.setsetting("../../../assets/image/Element/panel.png", windowWidth, windowHeight)) {
        settings.drawsetting(window);
    } else {
        std::cerr << "Failed to set setting" << std::endl;
    }
    
    window.display();
}

void WindowManager::handleEvent()
{
    while (window.pollEvent(event)) {
        if (event.type == sf::Event::Closed) {
            window.close();
        }
        ShapeManager shapeManager;
        shapeManager.drawRectangle(window, 100, 100, 100, 100, sf::Color::Red, 5);

        // get position of mouse
        MouseManager mouse;
        mouse.handleMousePosition(window);
        float x = mouse.getMouseX();
        float y = mouse.getMouseY();
        std::cout << "Mouse position: (" << x << ", " << y << ")" << std::endl;

        // ip input position: 666 165
        // port input position: 662 334
        // name input position: 670, 500
    } 
}

sf::RenderWindow &WindowManager::GetWindow() { return this->window; }

int main()
{
    WindowManager window(1920, 1080, "SFML window");
    window.keepOpen();
    return 0;
}
```


