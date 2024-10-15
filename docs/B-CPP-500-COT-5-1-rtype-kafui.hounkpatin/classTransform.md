

# Class Transform



[**ClassList**](annotated.md) **>** [**Transform**](classTransform.md)





* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  [**Vector2D**](classVector2D.md) | [**position**](#variable-position)   = = [**Vector2D**](classVector2D.md)(0, 0)<br>_Position of the entity._  |
|  [**Vector2D**](classVector2D.md) | [**velocity**](#variable-velocity)   = = [**Vector2D**](classVector2D.md)(0, 0)<br>_Velocity of the entity._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Transform**](#function-transform-12) () <br>_Default constructor initializes position and velocity to (0, 0)._  |
|   | [**Transform**](#function-transform-22) ([**Vector2D**](classVector2D.md) pos, [**Vector2D**](classVector2D.md) vel) <br>_Constructor to initialize position and velocity._  |




























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

```C++
inline Transform::Transform (
    Vector2D pos,
    Vector2D vel
) 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

