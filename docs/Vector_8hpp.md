

# File Vector.hpp



[**FileList**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Vector.hpp**](Vector_8hpp.md)

[Go to the source code of this file](Vector_8hpp_source.md)



* `#include <algorithm>`
* `#include <array>`
* `#include <cctype>`
* `#include <cmath>`
* `#include <fstream>`
* `#include <iostream>`
* `#include <limits>`
* `#include <map>`
* `#include <memory>`
* `#include <regex>`
* `#include <sstream>`
* `#include <stdexcept>`
* `#include <string>`
* `#include <tuple>`
* `#include <vector>`















## Classes

| Type | Name |
| ---: | :--- |
| class | [**Vector2D**](classVector2D.md) <br>_A class to represent a 2D vector._  |






















## Public Functions

| Type | Name |
| ---: | :--- |
|  [**Vector2D**](classVector2D.md) | [**operator\***](#function-operator) (double scalar, const [**Vector2D**](classVector2D.md) & v) <br>_Overloads the \* operator for scalar multiplication._  |
|  [**Vector2D**](classVector2D.md) | [**operator\***](#function-operator_1) (const [**Vector2D**](classVector2D.md) & v, int scalar) <br>_Overloads the \* operator for scalar multiplication._  |
|  [**Vector2D**](classVector2D.md) | [**operator+**](#function-operator_2) (const [**Vector2D**](classVector2D.md) & u, const [**Vector2D**](classVector2D.md) & v) <br>_Overloads the + operator for vector addition._  |
|  [**Vector2D**](classVector2D.md) | [**operator-**](#function-operator_3) (const [**Vector2D**](classVector2D.md) & p, const [**Vector2D**](classVector2D.md) & n) <br>_Overloads the - operator for vector subtraction._  |




























## Public Functions Documentation




### function operator\* 

_Overloads the \* operator for scalar multiplication._ 
```C++
Vector2D operator* (
    double scalar,
    const Vector2D & v
) 
```





**Parameters:**


* `scalar` The scalar to multiply the vector by. 
* `v` The vector to multiply. 



**Returns:**

The result of the scalar multiplication. 





        

<hr>



### function operator\* 

_Overloads the \* operator for scalar multiplication._ 
```C++
Vector2D operator* (
    const Vector2D & v,
    int scalar
) 
```





**Parameters:**


* `v` The vector to multiply. 
* `scalar` The scalar to multiply the vector by. 



**Returns:**

The result of the scalar multiplication. 





        

<hr>



### function operator+ 

_Overloads the + operator for vector addition._ 
```C++
Vector2D operator+ (
    const Vector2D & u,
    const Vector2D & v
) 
```





**Parameters:**


* `u` The first vector. 
* `v` The second vector. 



**Returns:**

The result of the vector addition. 





        

<hr>



### function operator- 

_Overloads the - operator for vector subtraction._ 
```C++
Vector2D operator- (
    const Vector2D & p,
    const Vector2D & n
) 
```





**Parameters:**


* `p` The first vector. 
* `n` The second vector. 



**Returns:**

The result of the vector subtraction. 





        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Vector.hpp`

