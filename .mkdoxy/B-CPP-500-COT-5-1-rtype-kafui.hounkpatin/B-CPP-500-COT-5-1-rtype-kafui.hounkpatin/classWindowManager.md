

# Class WindowManager



[**ClassList**](annotated.md) **>** [**WindowManager**](classWindowManager.md)





* `#include <WindowManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  sf::RenderWindow & | [**GetWindow**](#function-getwindow) () <br> |
|   | [**WindowManager**](#function-windowmanager) (int width, int height, const std::string & windowName) <br> |
|  void | [**drawTextTemporarily**](#function-drawtexttemporarily) (const std::string & text, float x, float y, sf::Color color, float duration) <br> |
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



### function WindowManager 

```C++
WindowManager::WindowManager (
    int width,
    int height,
    const std::string & windowName
) 
```




<hr>



### function drawTextTemporarily 

```C++
void WindowManager::drawTextTemporarily (
    const std::string & text,
    float x,
    float y,
    sf::Color color,
    float duration
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
The documentation for this class was generated from the following file `include/Engine/Window/WindowManager.hpp`

