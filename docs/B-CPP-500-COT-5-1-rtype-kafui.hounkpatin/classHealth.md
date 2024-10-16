

# Class Health



[**ClassList**](annotated.md) **>** [**Health**](classHealth.md)



_Component to manage an entity's health state._ [More...](#detailed-description)

* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  int | [**currentHealth**](#variable-currenthealth)  <br>_Current health of the entity._  |
|  int | [**maxHealth**](#variable-maxhealth)  <br>_Maximum health of the entity._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Health**](#function-health-12) () <br>_Default constructor initializes health to 0._  |
|   | [**Health**](#function-health-22) (int maxHp) <br>_Constructor to initialize the entity's health._  |
|  void | [**takeDamage**](#function-takedamage) (int damage) <br>_Reduces the current health by a specified amount._  |




























# Detailed Description


This component tracks both the maximum and current health of an entity. It is used to handle damage, healing, and health-based logic during gameplay. 


    
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

_Constructor to initialize the entity's health._ 
```C++
inline Health::Health (
    int maxHp
) 
```





**Parameters:**


* `maxHp` Maximum health of the entity. 




        

<hr>



### function takeDamage 

_Reduces the current health by a specified amount._ 
```C++
inline void Health::takeDamage (
    int damage
) 
```





**Parameters:**


* `damage` The amount of health to reduce. 



**Note:**

The health will not drop below 0. 





        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

