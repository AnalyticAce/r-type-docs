

# Class Name



[**ClassList**](annotated.md) **>** [**Name**](className.md)



_Component to store the name of an entity._ [More...](#detailed-description)

* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::string | [**name**](#variable-name)  <br>[_**Name**_](className.md) _of the entity._ |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Name**](#function-name-12) () <br>_Default constructor initializes the name to an empty string._  |
|   | [**Name**](#function-name-22) (std::string n) <br>_Constructor to set the name of the entity._  |




























# Detailed Description


This component is useful for distinguishing players, enemies, or specific in-game objects based on their names. 


    
## Public Attributes Documentation




### variable name 

```C++
std::string Name::name;
```




<hr>
## Public Functions Documentation




### function Name [1/2]

```C++
inline Name::Name () 
```




<hr>



### function Name [2/2]

_Constructor to set the name of the entity._ 
```C++
inline Name::Name (
    std::string n
) 
```





**Parameters:**


* `n` The name of the entity. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

