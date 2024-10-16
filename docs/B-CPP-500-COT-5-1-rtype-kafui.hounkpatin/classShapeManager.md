

# Class ShapeManager



[**ClassList**](annotated.md) **>** [**ShapeManager**](classShapeManager.md)



_Manages and renders geometric shapes using the SFML graphics library._ [More...](#detailed-description)

* `#include <ShapeManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**ShapeManager**](#function-shapemanager) () <br>_Constructs the_ [_**ShapeManager**_](classShapeManager.md) _instance._ |
|  void | [**drawCircle**](#function-drawcircle) (sf::RenderWindow & window, float x, float y, float radius, const sf::Color & color, float thickness) <br>_Renders a circle onto the provided SFML RenderWindow._  |
|  sf::RectangleShape | [**drawRectangle**](#function-drawrectangle) (sf::RenderWindow & window, float x, float y, float width, float height, sf::Color color, float outlineThickness, bool drawState=false) <br>_Renders a rectangle onto the provided SFML RenderWindow._  |
|   | [**~ShapeManager**](#function-shapemanager) () <br>_Destroys the_ [_**ShapeManager**_](classShapeManager.md) _instance._ |




























# Detailed Description


The [**ShapeManager**](classShapeManager.md) class encapsulates the functionality for drawing various geometric shapes (rectangles, circles, etc.) onto a given SFML render window.


This class is designed as a singleton, ensuring that only one instance manages all shape-rendering operations within the application. It provides an interface for creating and configuring shapes with specific properties such as position, dimensions, color, and border thickness.




**Note:**

This class is a non-copyable singleton, and it assumes that the SFML RenderWindow is properly initialized before invoking any shape drawing operations. 





    
## Public Functions Documentation




### function ShapeManager 

_Constructs the_ [_**ShapeManager**_](classShapeManager.md) _instance._
```C++
ShapeManager::ShapeManager () 
```



Initializes the [**ShapeManager**](classShapeManager.md) responsible for handling the rendering of shapes. 


        

<hr>



### function drawCircle 

_Renders a circle onto the provided SFML RenderWindow._ 
```C++
void ShapeManager::drawCircle (
    sf::RenderWindow & window,
    float x,
    float y,
    float radius,
    const sf::Color & color,
    float thickness
) 
```



This method draws a circle centered at the specified position (x, y) with the given radius, color, and border thickness.




**Parameters:**


* `window` Reference to the SFML RenderWindow where the shape will be drawn. 
* `x` Horizontal position of the circle's center. 
* `y` Vertical position of the circle's center. 
* `radius` Radius of the circle. 
* `color` Fill color of the circle. 
* `thickness` Thickness of the circle's border (outline).



**Note:**

The render window must be open and available before calling this function. 





        

<hr>



### function drawRectangle 

_Renders a rectangle onto the provided SFML RenderWindow._ 
```C++
sf::RectangleShape ShapeManager::drawRectangle (
    sf::RenderWindow & window,
    float x,
    float y,
    float width,
    float height,
    sf::Color color,
    float outlineThickness,
    bool drawState=false
) 
```



This method draws a rectangle at the specified position (x, y) with given dimensions (width, height) and a specified color and border thickness.




**Parameters:**


* `window` Reference to the SFML RenderWindow where the shape will be drawn. 
* `x` Horizontal position of the rectangle's top-left corner. 
* `y` Vertical position of the rectangle's top-left corner. 
* `width` Width of the rectangle. 
* `height` Height of the rectangle. 
* `color` Fill color of the rectangle. 
* `thickness` Thickness of the rectangle's border (outline).



**Note:**

The render window must be open and available before calling this function. 





        

<hr>



### function ~ShapeManager 

_Destroys the_ [_**ShapeManager**_](classShapeManager.md) _instance._
```C++
ShapeManager::~ShapeManager () 
```



Cleans up any resources held by the [**ShapeManager**](classShapeManager.md) before the instance is destroyed. 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Shape/ShapeManager.hpp`

