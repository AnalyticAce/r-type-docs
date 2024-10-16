

# Class Transform



[**ClassList**](annotated.md) **>** [**Transform**](classTransform.md)



_Component representing an entity's position and velocity in 2D space._ [More...](#detailed-description)

* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  [**Vector2D**](classVector2D.md) | [**position**](#variable-position)  <br>_Current position of the entity in 2D space._  |
|  [**Vector2D**](classVector2D.md) | [**velocity**](#variable-velocity)  <br>_Current velocity of the entity in 2D space._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Transform**](#function-transform-12) () <br>_Default constructor initializes position and velocity to (0, 0)._  |
|   | [**Transform**](#function-transform-22) ([**Vector2D**](classVector2D.md) pos, [**Vector2D**](classVector2D.md) vel) <br>_Constructor to initialize position and velocity._  |




























# Detailed Description


This component tracks the movement and spatial state of the entity. It is used for both static objects (e.g., obstacles) and dynamic entities (e.g., players).




**Note:**

The velocity can be used to determine how fast the entity moves over time. 





    
## Public Attributes Documentation




### variable position 

```C++
Vector2D Transform::position;
```




<hr>



### variable velocity 

```C++
Vector2D Transform::velocity;
```




<hr>
## Public Functions Documentation




### function Transform [1/2]

```C++
inline Transform::Transform () 
```




<hr>



### function Transform [2/2]

_Constructor to initialize position and velocity._ 
```C++
inline Transform::Transform (
    Vector2D pos,
    Vector2D vel
) 
```





**Parameters:**


* `pos` Initial position of the entity. 
* `vel` Initial velocity of the entity. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

