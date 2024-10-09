

# Class CollisionSystem



[**ClassList**](annotated.md) **>** [**CollisionSystem**](classCollisionSystem.md)





* `#include <Collision_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**CollisionSystem**](#function-collisionsystem) () <br> |
|  bool | [**check\_collision**](#function-check_collision) (std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; & proj, std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; & enemy) <br> |
|  void | [**collision\_enemy\_projectiles**](#function-collision_enemy_projectiles) ([**Registry**](classRegistry.md) & registry) <br> |
|  void | [**collision\_player\_enemy**](#function-collision_player_enemy) ([**Registry**](classRegistry.md) & registry) <br> |
|  void | [**collison\_player\_coins**](#function-collison_player_coins) ([**Registry**](classRegistry.md) & registry) <br> |
|   | [**~CollisionSystem**](#function-collisionsystem) () <br> |




























## Public Functions Documentation




### function CollisionSystem 

```C++
inline CollisionSystem::CollisionSystem () 
```




<hr>



### function check\_collision 

```C++
bool CollisionSystem::check_collision (
    std::shared_ptr< Entity > & proj,
    std::shared_ptr< Entity > & enemy
) 
```




<hr>



### function collision\_enemy\_projectiles 

```C++
void CollisionSystem::collision_enemy_projectiles (
    Registry & registry
) 
```




<hr>



### function collision\_player\_enemy 

```C++
void CollisionSystem::collision_player_enemy (
    Registry & registry
) 
```




<hr>



### function collison\_player\_coins 

```C++
void CollisionSystem::collison_player_coins (
    Registry & registry
) 
```




<hr>



### function ~CollisionSystem 

```C++
inline CollisionSystem::~CollisionSystem () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/include/Collision_system.hpp`

