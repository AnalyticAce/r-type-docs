

# Class InputManager



[**ClassList**](annotated.md) **>** [**InputManager**](classInputManager.md)



_Manages keyboard and window input events using the SFML library._ [More...](#detailed-description)

* `#include <InputManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**InputManager**](#function-inputmanager) () <br>_Constructs an_ [_**InputManager**_](classInputManager.md) _instance._ |
|  Button | [**getButton**](#function-getbutton) (void) const<br>_Retrieves the current button states._  |
|  void | [**handleInput**](#function-handleinput) (sf::Event event, sf::RenderWindow & window) <br>_Handles input events from the window._  |
|   | [**~InputManager**](#function-inputmanager) () <br>_Destructs the_ [_**InputManager**_](classInputManager.md) _instance._ |




























# Detailed Description


The [**InputManager**](classInputManager.md) class is responsible for handling user input, including keyboard events and window-related events (e.g., closing the window). It provides an interface to track specific key presses and allows easy retrieval of button states. 


    
## Public Functions Documentation




### function InputManager 

_Constructs an_ [_**InputManager**_](classInputManager.md) _instance._
```C++
InputManager::InputManager () 
```



Initializes the [**InputManager**](classInputManager.md) and sets up the internal button state. 


        

<hr>



### function getButton 

_Retrieves the current button states._ 
```C++
Button InputManager::getButton (
    void
) const
```



Returns a copy of the Button structure containing the current states of all tracked buttons.




**Returns:**

A Button struct with the state of the control buttons. 





        

<hr>



### function handleInput 

_Handles input events from the window._ 
```C++
void InputManager::handleInput (
    sf::Event event,
    sf::RenderWindow & window
) 
```



Processes the given SFML event and updates the internal button states based on key presses or releases. It also handles window-specific events such as closing.




**Parameters:**


* `event` The SFML event to process (e.g., key press or release). 
* `window` The SFML render window where the event is coming from. 




        

<hr>



### function ~InputManager 

_Destructs the_ [_**InputManager**_](classInputManager.md) _instance._
```C++
InputManager::~InputManager () 
```



Cleans up any resources used for input handling. Since no dynamic memory is allocated, this primarily exists for completeness. 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Input/InputManager.hpp`

