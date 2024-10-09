

# Class Animation



[**ClassList**](annotated.md) **>** [**Animation**](classAnimation.md)





* `#include <Animation.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Animation**](#function-animation) () <br> |
|  sf::Sprite & | [**getSprite**](#function-getsprite) () <br> |
|  void | [**loadAnimation**](#function-loadanimation) (const std::string & name\_by\_color, int frames) <br> |
|  void | [**moveXLeft**](#function-movexleft) (const std::string & name\_by\_color, float SpeedX) <br> |
|  void | [**moveXRight**](#function-movexright) (const std::string & name\_by\_color, float SpeedX) <br> |
|  void | [**moveY**](#function-movey) (const std::string & name\_by\_color, float SpeedY) <br> |
|  void | [**moveYUp**](#function-moveyup) (const std::string & name\_by\_color, float SpeedY) <br> |
|  void | [**render**](#function-render) (sf::RenderWindow & window, const std::string & name\_by\_color) <br> |
|  void | [**setPosition**](#function-setposition) (const std::string & name\_by\_color, float x, float y) <br> |
|  void | [**setScale**](#function-setscale) (float scaleX, float scaleY) <br> |
|  void | [**update**](#function-update) (const std::string & name\_by\_color) <br> |
|   | [**~Animation**](#function-animation) () <br> |




























## Public Functions Documentation




### function Animation 

```C++
Animation::Animation () 
```




<hr>



### function getSprite 

```C++
inline sf::Sprite & Animation::getSprite () 
```




<hr>



### function loadAnimation 

```C++
void Animation::loadAnimation (
    const std::string & name_by_color,
    int frames
) 
```




<hr>



### function moveXLeft 

```C++
void Animation::moveXLeft (
    const std::string & name_by_color,
    float SpeedX
) 
```




<hr>



### function moveXRight 

```C++
void Animation::moveXRight (
    const std::string & name_by_color,
    float SpeedX
) 
```




<hr>



### function moveY 

```C++
void Animation::moveY (
    const std::string & name_by_color,
    float SpeedY
) 
```




<hr>



### function moveYUp 

```C++
void Animation::moveYUp (
    const std::string & name_by_color,
    float SpeedY
) 
```




<hr>



### function render 

```C++
void Animation::render (
    sf::RenderWindow & window,
    const std::string & name_by_color
) 
```




<hr>



### function setPosition 

```C++
void Animation::setPosition (
    const std::string & name_by_color,
    float x,
    float y
) 
```




<hr>



### function setScale 

```C++
void Animation::setScale (
    float scaleX,
    float scaleY
) 
```




<hr>



### function update 

```C++
void Animation::update (
    const std::string & name_by_color
) 
```




<hr>



### function ~Animation 

```C++
Animation::~Animation () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Animation/Animation.hpp`

