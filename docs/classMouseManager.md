

# Class MouseManager



[**ClassList**](annotated.md) **>** [**MouseManager**](classMouseManager.md)



_Manages mouse input and tracks the mouse position within a window._ [More...](#detailed-description)

* `#include <MouseManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**MouseManager**](#function-mousemanager) () <br>_Constructs a_ [_**MouseManager**_](classMouseManager.md) _instance._ |
|  float | [**getMouseX**](#function-getmousex) () const<br>_Retrieves the current X coordinate of the mouse._  |
|  float | [**getMouseY**](#function-getmousey) () const<br>_Retrieves the current Y coordinate of the mouse._  |
|  void | [**handleMousePosition**](#function-handlemouseposition) (sf::RenderWindow & window) <br>_Updates the mouse position within the given window._  |
|   | [**~MouseManager**](#function-mousemanager) () <br>_Destructs the_ [_**MouseManager**_](classMouseManager.md) _instance._ |




























# Detailed Description


The [**MouseManager**](classMouseManager.md) class provides functionality to track the mouse's position within an SFML render window. It retrieves and stores the current mouse coordinates (x, y) in real-time and provides access to these coordinates for further use. 


    
## Public Functions Documentation




### function MouseManager 

_Constructs a_ [_**MouseManager**_](classMouseManager.md) _instance._
```C++
MouseManager::MouseManager () 
```



Initializes the [**MouseManager**](classMouseManager.md), setting the initial mouse coordinates to zero. 


        

<hr>



### function getMouseX 

_Retrieves the current X coordinate of the mouse._ 
```C++
float MouseManager::getMouseX () const
```



Returns the stored horizontal mouse position relative to the window.




**Returns:**

A float representing the current X coordinate of the mouse. 





        

<hr>



### function getMouseY 

_Retrieves the current Y coordinate of the mouse._ 
```C++
float MouseManager::getMouseY () const
```



Returns the stored vertical mouse position relative to the window.




**Returns:**

A float representing the current Y coordinate of the mouse. 





        

<hr>



### function handleMousePosition 

_Updates the mouse position within the given window._ 
```C++
void MouseManager::handleMousePosition (
    sf::RenderWindow & window
) 
```



Retrieves the current position of the mouse relative to the provided SFML window and updates the internal x and y values accordingly.




**Parameters:**


* `window` The SFML render window from which the mouse position is retrieved. 




        

<hr>



### function ~MouseManager 

_Destructs the_ [_**MouseManager**_](classMouseManager.md) _instance._
```C++
MouseManager::~MouseManager () 
```



Cleans up any resources used for mouse input handling. Since no dynamic memory is allocated, this primarily exists for completeness. 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Mouse/MouseManager.hpp`

