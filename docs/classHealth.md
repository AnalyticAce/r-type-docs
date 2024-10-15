

# Class Health



[**ClassList**](annotated.md) **>** [**Health**](classHealth.md)





* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  int | [**currentHealth**](#variable-currenthealth)  <br>_Current health of the entity._  |
|  int | [**maxHealth**](#variable-maxhealth)  <br>_Maximum health of the entity._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Health**](#function-health-12) () <br>_Default constructor initializes both max and current health to 0._  |
|   | [**Health**](#function-health-22) (int maxHp) <br>_Constructor to initialize with a specific max health._  |
|  void | [**takeDamage**](#function-takedamage) (int damage) <br> |




























## Public Attributes Documentation




### variable currentHealth 

```C++
int Health::currentHealth;
```




<hr>



### variable maxHealth 

```C++
int Health::maxHealth;
```




<hr>
## Public Functions Documentation




### function Health [1/2]

```C++
inline Health::Health () 
```




<hr>



### function Health [2/2]

```C++
inline Health::Health (
    int maxHp
) 
```




<hr>



### function takeDamage 


```C++
inline void Health::takeDamage (
    int damage
) 
```



Reduces the entity's health by the specified amount. 

**Parameters:**


* `damage` The amount of damage to subtract. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

