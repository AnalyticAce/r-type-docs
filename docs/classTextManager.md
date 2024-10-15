

# Class TextManager



[**ClassList**](annotated.md) **>** [**TextManager**](classTextManager.md)





* `#include <InputManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  sf::RenderWindow & | [**GetWindow**](#function-getwindow) () <br> |
|   | [**TextManager**](#function-textmanager) () <br> |
|  void | [**drawText**](#function-drawtext) (const std::string & text, float x, float y, sf::Color color, sf::RenderWindow & window) <br> |
|  void | [**drawTextTemporarily**](#function-drawtexttemporarily) (const std::string & text, float x, float y, sf::Color color, float duration, sf::RenderWindow & window) <br> |
|  void | [**handleEvent**](#function-handleevent) () <br> |
|  void | [**loadFont**](#function-loadfont) (const std::string & fontPath) <br> |
|  void | [**render**](#function-render) () <br> |




























## Public Functions Documentation




### function GetWindow 

```C++
sf::RenderWindow & TextManager::GetWindow () 
```




<hr>



### function TextManager 

```C++
inline TextManager::TextManager () 
```




<hr>



### function drawText 

```C++
void TextManager::drawText (
    const std::string & text,
    float x,
    float y,
    sf::Color color,
    sf::RenderWindow & window
) 
```




<hr>



### function drawTextTemporarily 

```C++
void TextManager::drawTextTemporarily (
    const std::string & text,
    float x,
    float y,
    sf::Color color,
    float duration,
    sf::RenderWindow & window
) 
```




<hr>



### function handleEvent 

```C++
void TextManager::handleEvent () 
```




<hr>



### function loadFont 

```C++
void TextManager::loadFont (
    const std::string & fontPath
) 
```




<hr>



### function render 

```C++
void TextManager::render () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Input/InputManager.hpp`

