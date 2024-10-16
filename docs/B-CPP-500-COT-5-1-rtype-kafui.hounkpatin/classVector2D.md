

# Class Vector2D



[**ClassList**](annotated.md) **>** [**Vector2D**](classVector2D.md)



_A class to represent a 2D vector._ 

* `#include <Vector.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  double | [**x**](#variable-x)  <br>_The x component of the vector._  |
|  double | [**y**](#variable-y)  <br>_The y component of the vector._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Vector2D**](#function-vector2d-12) () <br>_Default constructor. Initializes the vector to (0,0,0)._  |
|   | [**Vector2D**](#function-vector2d-22) (double x, double y) <br>_Constructor with parameters._  |
|  [**Vector2D**](classVector2D.md) & | [**add**](#function-add) (const [**Vector2D**](classVector2D.md) & v) <br> |
|  double | [**dot**](#function-dot) (const [**Vector2D**](classVector2D.md) & other) const<br>_Calculates the dot product with another vector._  |
|  double | [**length**](#function-length) () const<br>_Calculates the length of the vector._  |
|  double | [**length\_squared**](#function-length_squared) () const<br>_Calculates the squared length of the vector._  |
|  [**Vector2D**](classVector2D.md) | [**normalize**](#function-normalize) () <br>_Normalizes a vector._  |
|  [**Vector2D**](classVector2D.md) | [**operator/**](#function-operator) (double scalar) const<br>_Overloads the / operator for scalar division._  |
|  [**Vector2D**](classVector2D.md) & | [**operator/=**](#function-operator_1) (double scalar) <br>_Overloads the /= operator for scalar division._  |
|  [**Vector2D**](classVector2D.md) & | [**rotate**](#function-rotate) (double angle) <br> |
|  [**Vector2D**](classVector2D.md) & | [**scale**](#function-scale) (double scalar) <br>_scale the vector by a scalar_  |
|  [**Vector2D**](classVector2D.md) | [**vector\_unit**](#function-vector_unit) () const<br>_Calculates the unit vector._  |




























## Public Attributes Documentation




### variable x 

```C++
double Vector2D::x;
```




<hr>



### variable y 

```C++
double Vector2D::y;
```




<hr>
## Public Functions Documentation




### function Vector2D [1/2]

```C++
inline Vector2D::Vector2D () 
```




<hr>



### function Vector2D [2/2]

_Constructor with parameters._ 
```C++
inline Vector2D::Vector2D (
    double x,
    double y
) 
```





**Parameters:**


* `x` The x component of the vector. 
* `y` The y component of the vector. 




        

<hr>



### function add 

```C++
inline Vector2D & Vector2D::add (
    const Vector2D & v
) 
```




<hr>



### function dot 

_Calculates the dot product with another vector._ 
```C++
inline double Vector2D::dot (
    const Vector2D & other
) const
```





**Parameters:**


* `other` The other vector. 



**Returns:**

The dot product. 





        

<hr>



### function length 

_Calculates the length of the vector._ 
```C++
inline double Vector2D::length () const
```





**Returns:**

The length of the vector. 





        

<hr>



### function length\_squared 

_Calculates the squared length of the vector._ 
```C++
inline double Vector2D::length_squared () const
```





**Returns:**

The squared length of the vector. 





        

<hr>



### function normalize 

_Normalizes a vector._ 
```C++
inline Vector2D Vector2D::normalize () 
```





**Parameters:**


* `v` The vector to normalize. 



**Returns:**

The normalized vector. 





        

<hr>



### function operator/ 

_Overloads the / operator for scalar division._ 
```C++
inline Vector2D Vector2D::operator/ (
    double scalar
) const
```





**Parameters:**


* `scalar` The scalar to divide the vector by. 



**Returns:**

A new vector that is the result of the division. 





        

<hr>



### function operator/= 

_Overloads the /= operator for scalar division._ 
```C++
inline Vector2D & Vector2D::operator/= (
    double scalar
) 
```





**Parameters:**


* `scalar` The scalar to divide the vector by. 



**Returns:**

The vector itself after division. 





        

<hr>



### function rotate 

```C++
inline Vector2D & Vector2D::rotate (
    double angle
) 
```




<hr>



### function scale 

_scale the vector by a scalar_ 
```C++
inline Vector2D & Vector2D::scale (
    double scalar
) 
```





**Parameters:**


* `scalar` 



**Returns:**

[**Vector2D**](classVector2D.md)& 





        

<hr>



### function vector\_unit 

_Calculates the unit vector._ 
```C++
inline Vector2D Vector2D::vector_unit () const
```





**Returns:**

The unit vector. 





        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Vector.hpp`

