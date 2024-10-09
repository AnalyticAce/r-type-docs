

# File TextField.cpp

[**File List**](files.md) **>** [**Engine**](dir_3072bc1f55ed1280fe4fbe6b21c78379.md) **>** [**Input**](dir_cc001759347ed62121aae3ac8586610a.md) **>** [**TextField.cpp**](TextField_8cpp.md)

[Go to the documentation of this file](TextField_8cpp.md)


```C++
// #include <SFML/Graphics.hpp>

// int main() 
// {
//     sf::RenderWindow window(sf::VideoMode(800,600),"Window", 
//     sf::Style::Titlebar | sf::Style::Close);
//     sf::Font arial;
//     arial.loadFromFile("../assets/font/EduAUVICWANTDots-Bold.ttf");
//     sf::Text t;
//     t.setFillColor(sf::Color::White);
//     t.setFont(arial);
//     std::string s = "This is text that you type: ";
//     t.setString(s);

//     while(window.isOpen()){
//         sf::Event event;

//         while(window.pollEvent(event)){
//             if(event.type == sf::Event::Closed){
//                 window.close();
//             }
//             if(event.type == sf::Event::TextEntered){
//                 s.append(std::to_string(event.key.code));
//             }
//         }
//         t.setString(s);
//         window.clear(sf::Color::Black);
//         window.draw(t);
//         window.display();
//     }
// }
```


