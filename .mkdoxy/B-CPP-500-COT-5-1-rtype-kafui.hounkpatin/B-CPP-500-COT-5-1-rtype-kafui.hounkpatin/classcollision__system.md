

# Class collision\_system



[**ClassList**](annotated.md) **>** [**collision\_system**](classcollision__system.md)





* `#include <Collision_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**check\_collision**](#function-check_collision) (std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; & proj, std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; & enemy) <br> |
|  void | [**collision\_enemy\_projectiles**](#function-collision_enemy_projectiles) ([**Registry**](classRegistry.md) & registry) <br> |
|  void | [**collision\_player\_enemy**](#function-collision_player_enemy) ([**Registry**](classRegistry.md) & registry) <br> |
|   | [**collision\_system**](#function-collision_system) () <br> |
|  void | [**collison\_player\_coins**](#function-collison_player_coins) ([**Registry**](classRegistry.md) & registry) <br> |
|   | [**~collision\_system**](#function-collision_system) () <br> |




























## Public Functions Documentation




### function check\_collision 

```C++
bool collision_system::check_collision (
    std::shared_ptr< Entity > & proj,
    std::shared_ptr< Entity > & enemy
) 
```




<hr>



### function collision\_enemy\_projectiles 

```C++
void collision_system::collision_enemy_projectiles (
    Registry & registry
) 
```




<hr>



### function collision\_player\_enemy 

```C++
void collision_system::collision_player_enemy (
    Registry & registry
) 
```




<hr>



### function collision\_system 

```C++
inline collision_system::collision_system () 
```




<hr>



### function collison\_player\_coins 

```C++
void collision_system::collison_player_coins (
    Registry & registry
) 
```




<hr>



### function ~collision\_system 

```C++
inline collision_system::~collision_system () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/GameLogic/Collision_system.hpp`

