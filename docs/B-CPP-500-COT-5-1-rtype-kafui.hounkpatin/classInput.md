

# Class Input



[**ClassList**](annotated.md) **>** [**Input**](classInput.md)



_Component to track player input actions (e.g., movement or shooting)._ [More...](#detailed-description)

* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  bool | [**down**](#variable-down)  <br>_Whether the 'down' key is pressed._  |
|  bool | [**left**](#variable-left)  <br>_Whether the 'left' key is pressed._  |
|  bool | [**right**](#variable-right)  <br>_Whether the 'right' key is pressed._  |
|  bool | [**shoot**](#variable-shoot)  <br>_Whether the 'shoot' action is performed._  |
|  bool | [**up**](#variable-up)  <br>_Whether the 'up' key is pressed._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Input**](#function-input) () <br>_Default constructor initializes all input actions to false._  |
|  void | [**reset**](#function-reset) () <br>_Resets all input actions to false._  |




























# Detailed Description


This component helps manage input events such as pressing keys or performing actions. It is typically associated with player-controlled entities. 


    
## Public Attributes Documentation




### variable down 

```C++
bool Input::down;
```




<hr>



### variable left 

```C++
bool Input::left;
```




<hr>



### variable right 

```C++
bool Input::right;
```




<hr>



### variable shoot 

```C++
bool Input::shoot;
```




<hr>



### variable up 

```C++
bool Input::up;
```




<hr>
## Public Functions Documentation




### function Input 

```C++
inline Input::Input () 
```




<hr>



### function reset 

```C++
inline void Input::reset () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

