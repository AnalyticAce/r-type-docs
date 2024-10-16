

# Class BBox



[**ClassList**](annotated.md) **>** [**BBox**](classBBox.md)



_Component representing the size of an entity's bounding box._ [More...](#detailed-description)

* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  [**Vector2D**](classVector2D.md) | [**size**](#variable-size)  <br>_Size of the entity's bounding box._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**BBox**](#function-bbox-12) () <br>_Default constructor initializes the bounding box size to (0, 0)._  |
|   | [**BBox**](#function-bbox-22) ([**Vector2D**](classVector2D.md) s) <br>_Constructor to set the bounding box size._  |




























# Detailed Description


This component is useful for collision detection, determining how much space the entity occupies in the game world. 


    
## Public Attributes Documentation




### variable size 

```C++
Vector2D BBox::size;
```




<hr>
## Public Functions Documentation




### function BBox [1/2]

```C++
inline BBox::BBox () 
```




<hr>



### function BBox [2/2]

_Constructor to set the bounding box size._ 
```C++
inline BBox::BBox (
    Vector2D s
) 
```





**Parameters:**


* `s` The size of the bounding box. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

