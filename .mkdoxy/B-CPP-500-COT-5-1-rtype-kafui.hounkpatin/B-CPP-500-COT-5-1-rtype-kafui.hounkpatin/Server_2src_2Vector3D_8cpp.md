

# File Vector3D.cpp



[**FileList**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**Vector3D.cpp**](Server_2src_2Vector3D_8cpp.md)

[Go to the source code of this file](Server_2src_2Vector3D_8cpp_source.md)



* `#include "../include/Vector.hpp"`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  [**Vector2D**](classVector2D.md) | [**operator\***](#function-operator) (double scalar, const [**Vector2D**](classVector2D.md) & v) <br>_Overloads the \* operator for scalar multiplication._  |
|  [**Vector2D**](classVector2D.md) | [**operator\***](#function-operator_1) (const [**Vector2D**](classVector2D.md) & v, int scalar) <br>_Overloads the \* operator for scalar multiplication._  |
|  [**Vector2D**](classVector2D.md) | [**operator\*=**](#function-operator_2) ([**Vector2D**](classVector2D.md) & v, double scalar) <br> |
|  [**Vector2D**](classVector2D.md) | [**operator+**](#function-operator_3) (const [**Vector2D**](classVector2D.md) & u, const [**Vector2D**](classVector2D.md) & v) <br>_Overloads the + operator for vector addition._  |
|  [**Vector2D**](classVector2D.md) | [**operator-**](#function-operator_4) (const [**Vector2D**](classVector2D.md) & p, const [**Vector2D**](classVector2D.md) & n) <br>_Overloads the - operator for vector subtraction._  |




























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



### function operator\*= 

```C++
Vector2D operator*= (
    Vector2D & v,
    double scalar
) 
```




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
The documentation for this class was generated from the following file `src/Server/src/Vector3D.cpp`

