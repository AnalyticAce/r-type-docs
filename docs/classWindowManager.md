

# Class WindowManager



[**ClassList**](annotated.md) **>** [**WindowManager**](classWindowManager.md)





* `#include <MenuWindowManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  sf::RenderWindow & | [**GetWindow**](#function-getwindow) () <br> |
|  void | [**SetWindowSize**](#function-setwindowsize) (const sf::Vector2u & size) <br> |
|   | [**WindowManager**](#function-windowmanager) (int width, int height, const std::string & windowName) <br> |
|  void | [**drawText**](#function-drawtext) (const std::string & text, float x, float y, sf::Color color) <br> |
|  void | [**handleEvent**](#function-handleevent) () <br> |
|  void | [**keepOpen**](#function-keepopen) () <br> |
|  void | [**loadFont**](#function-loadfont) (const std::string & fontPath) <br> |
|  void | [**render**](#function-render) () <br> |




























## Public Functions Documentation




### function GetWindow 

```C++
sf::RenderWindow & WindowManager::GetWindow () 
```




<hr>



### function SetWindowSize 

```C++
void WindowManager::SetWindowSize (
    const sf::Vector2u & size
) 
```




<hr>



### function WindowManager 

```C++
WindowManager::WindowManager (
    int width,
    int height,
    const std::string & windowName
) 
```




<hr>



### function drawText 

```C++
void WindowManager::drawText (
    const std::string & text,
    float x,
    float y,
    sf::Color color
) 
```




<hr>



### function handleEvent 

```C++
void WindowManager::handleEvent () 
```




<hr>



### function keepOpen 

```C++
void WindowManager::keepOpen () 
```




<hr>



### function loadFont 

```C++
void WindowManager::loadFont (
    const std::string & fontPath
) 
```




<hr>



### function render 

```C++
void WindowManager::render () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/Save/MenuWindowManager.hpp`

