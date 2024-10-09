

# File WindowManager.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Window**](dir_4681a19507fe33ded8545b89b782904d.md) **>** [**WindowManager.cpp**](WindowManager_8cpp.md)

[Go to the documentation of this file](WindowManager_8cpp.md)


```C++
#include "../../../include/Engine/Window/WindowManager.hpp"

WindowManager::WindowManager(int width, int height,
                             const std::string &windowName)
    : window(sf::VideoMode(width, height), windowName)

{
  animation.loadAnimation("red", 16);
  animation.loadAnimation("gray", 6);
}

void WindowManager::keepOpen() {
  animation.setPosition("red", 100.0f, 200.0f);
  animation.setPosition("gray", 300.0f, 400.0f);

  while (window.isOpen()) {
    animation.update("red");
    animation.update("gray");
    handleEvent();
    render();
  }
}

void WindowManager::drawText(const std::string &text, float x, float y,
                             sf::Color color) {
  sf::Text sfText;
  sfText.setFont(font);
  sfText.setString(text);
  sfText.setPosition(x, y);
  sfText.setFillColor(color);
  window.draw(sfText);
}

void WindowManager::drawTextTemporarily(const std::string &text, float x,
                                        float y, sf::Color color,
                                        float duration) {

  TemporaryText tempText;
  tempText.text.setFont(font);
  tempText.text.setString(text);
  tempText.text.setPosition(x, y);
  tempText.text.setFillColor(color);
  tempText.duration = duration;
  tempText.clock.restart();
  tempTexts.push_back(tempText);
}

void WindowManager::loadFont(const std::string &fontPath) {
  if (!font.loadFromFile(fontPath)) {
  }
}

void draw_shape(const std::string &ShapeName, sf::RenderWindow &window,
                float x = 0.0f, float y = 0.0f, float size = 50.0f,
                sf::Color color = sf::Color::White,
                sf::Color outlineColor = sf::Color::Black,
                float outlineThickness = 0.0f) {
  if (ShapeName == "rectangle") {
    sf::RectangleShape rectangle(sf::Vector2f(size, size));
    rectangle.setPosition(x, y);
    rectangle.setFillColor(color);
    rectangle.setOutlineColor(outlineColor);
    rectangle.setOutlineThickness(outlineThickness);
    window.draw(rectangle);
  } else if (ShapeName == "circle") {
    sf::CircleShape circle(size / 2);
    circle.setPosition(x, y);
    circle.setFillColor(color);
    circle.setOutlineColor(outlineColor);
    circle.setOutlineThickness(outlineThickness);
    window.draw(circle);
  }
}

void WindowManager::render() {
  window.clear(sf::Color::Black);

  //window.draw(animation.getSprite());
  animation.render(window, "red");
  animation.render(window, "gray");

  sf::RectangleShape rectangle(sf::Vector2f(100, 100));
  draw_shape("rectangle", window, 100, 100, 50, sf::Color::Red,
             sf::Color::Green, 1);
  draw_shape("circle", window, 200, 200, 50, sf::Color::Blue, sf::Color::Yellow,
             1);
  drawText("It works", 480, 240, sf::Color::Yellow);

  for (auto it = tempTexts.begin(); it != tempTexts.end();) {
    if (it->clock.getElapsedTime().asSeconds() < it->duration) {
      window.draw(it->text);
      ++it;
    } else {
      it = tempTexts.erase(it);
    }
  }
  window.display();
}

void WindowManager::handleEvent() {
  while (window.pollEvent(event)) {
    if (event.type == sf::Event::Closed) {
      window.close();
    }

    /*dear worker : input can be managed here.
    you can decide to put it anywhere. be sur that it work*/

    /*input.handleInput(event, window);

    if (input.getButton().down == true) {
      animation.moveY("red", 5);
      std::cout << "Down button pressed" << std::endl;
    } if (input.getButton().up == true) {
      animation.moveYUp("red", 5);
      std::cout << "Up button pressed" << std::endl;
    } if (input.getButton().left == true) {
      animation.moveXLeft("red", 5);
      std::cout << "Left button pressed" << std::endl;
    } if (input.getButton().right == true) {
      animation.moveXRight("red", 5);
      std::cout << "Right button pressed" << std::endl;
    }*/

    // mouse.handleMousePosition(window);
  }
}

sf::RenderWindow &WindowManager::GetWindow() { return this->window; }

/*int main() {
  WindowManager WindowManager(1500, 700, "R type window");
  WindowManager.loadFont("../../../assets/font/EduAUVICWANTDots-Bold.ttf");
  WindowManager.drawTextTemporarily("Temporary text", 480, 300,
                                    sf::Color::Green, 3.0f);
  WindowManager.drawTextTemporarily("Temporary 2", 480, 380, sf::Color::Yellow,
                                    6.0f);
  WindowManager.drawTextTemporarily("Temporary 3", 480, 430, sf::Color::Yellow,
                                    9.0f);
  WindowManager.drawTextTemporarily("Temporary 4", 480, 480, sf::Color::Yellow,
                                    12.0f);
  WindowManager.drawTextTemporarily("Temporary 5", 480, 530, sf::Color::Yellow,
                                    15.0f);
  WindowManager.keepOpen();
}
*/
/*
g++ WindowManager.cpp ../Input/InputManager.cpp ../Mouse/MouseManager.cpp 
../Animation/Animation.cpp -o open_window -lsfml-graphics -lsfml-window -lsfml-system
*/
```


