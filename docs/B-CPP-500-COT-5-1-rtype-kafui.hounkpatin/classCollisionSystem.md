

# Class CollisionSystem



[**ClassList**](annotated.md) **>** [**CollisionSystem**](classCollisionSystem.md)



_Handles collision detection and responses in the ECS (_ [_**Entity**_](classEntity.md) _Component System)._[More...](#detailed-description)

* `#include <Collision_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**CollisionSystem**](#function-collisionsystem) () <br>_Default constructor for the_ [_**CollisionSystem**_](classCollisionSystem.md) _. Initializes the collision system but currently does not require any specific setup._ |
|  bool | [**check\_collision**](#function-check_collision) (std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; & proj, std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; & enemy) <br>_Checks if a collision occurred between two entities._  |
|  bool | [**collision\_enemy\_projectiles**](#function-collision_enemy_projectiles) ([**Registry**](classRegistry.md) & registry) <br>_Handles collisions between enemy entities and projectiles._  |
|  void | [**collision\_player\_enemy**](#function-collision_player_enemy) ([**Registry**](classRegistry.md) & registry) <br>_Handles collisions between the player and enemies._  |
|  void | [**collison\_player\_coins**](#function-collison_player_coins) ([**Registry**](classRegistry.md) & registry) <br>_Handles interactions between the player and coins._  |
|   | [**~CollisionSystem**](#function-collisionsystem) () <br>_Default destructor for the_ [_**CollisionSystem**_](classCollisionSystem.md) _. Ensures proper cleanup of any allocated resources, though none are explicitly required here._ |




























# Detailed Description


This system manages various types of collisions, such as player-enemy collisions, player-coin interactions, and enemy-projectile collisions. It utilizes the ECS registry to access and modify entity states and interactions. 


    
## Public Functions Documentation




### function CollisionSystem 

```C++
inline CollisionSystem::CollisionSystem () 
```




<hr>



### function check\_collision 

_Checks if a collision occurred between two entities._ 
```C++
bool CollisionSystem::check_collision (
    std::shared_ptr< Entity > & proj,
    std::shared_ptr< Entity > & enemy
) 
```



This method determines if a collision has occurred between a projectile and an enemy entity. It returns `true` if a collision is detected and `false` otherwise.




**Parameters:**


* `proj` Shared pointer to the projectile entity involved in the potential collision. 
* `enemy` Shared pointer to the enemy entity involved in the potential collision. 



**Returns:**

`true` if a collision is detected, `false` otherwise. 





        

<hr>



### function collision\_enemy\_projectiles 

_Handles collisions between enemy entities and projectiles._ 
```C++
bool CollisionSystem::collision_enemy_projectiles (
    Registry & registry
) 
```



This method checks if any projectiles have hit enemies, applying damage and potentially removing either the enemy or the projectile based on game logic.




**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) object containing all entities and components. 




        

<hr>



### function collision\_player\_enemy 

_Handles collisions between the player and enemies._ 
```C++
void CollisionSystem::collision_player_enemy (
    Registry & registry
) 
```



This function detects if the player has collided with any enemy entities and updates the state accordingly (e.g., reducing player health, triggering death animations, etc.).




**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) object containing all entities and components. 




        

<hr>



### function collison\_player\_coins 

_Handles interactions between the player and coins._ 
```C++
void CollisionSystem::collison_player_coins (
    Registry & registry
) 
```



Detects if the player has collected any coins and updates the game state, such as increasing the player's coin count or triggering a reward.




**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) object containing all entities and components. 




        

<hr>



### function ~CollisionSystem 

```C++
inline CollisionSystem::~CollisionSystem () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Collision_system.hpp`

