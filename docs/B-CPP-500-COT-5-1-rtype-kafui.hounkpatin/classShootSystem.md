

# Class ShootSystem



[**ClassList**](annotated.md) **>** [**ShootSystem**](classShootSystem.md)



_&lt; Includes the_ [_**Entity**_](classEntity.md) _class for representing game entities._[More...](#detailed-description)

* `#include <Shoot_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  [**Vector2D**](classVector2D.md) | [**spawn\_projectile**](#function-spawn_projectile) ([**Registry**](classRegistry.md) & registry, [**Entity**](classEntity.md) & player) <br>_Spawns a projectile based on the player's current position and direction._  |




























# Detailed Description


A system responsible for handling the shooting mechanics of entities, particularly players.


The [**ShootSystem**](classShootSystem.md) class provides a function to spawn projectiles in the game. It takes in the game registry, which manages all entities and components, and the player entity that initiates the projectile. The system is designed to spawn projectiles at the player's current position, aiming or moving in the intended direction. 


    
## Public Functions Documentation




### function spawn\_projectile 

_Spawns a projectile based on the player's current position and direction._ 
```C++
Vector2D ShootSystem::spawn_projectile (
    Registry & registry,
    Entity & player
) 
```



This function creates a projectile entity and sets its initial position, which is usually near or at the player's current position. The function interacts with the game's registry to store the newly created projectile entity and initialize it with relevant components (such as position, velocity, etc.).




**Parameters:**


* `registry` Reference to the game's entity-component-system (ECS) registry. The registry is used to manage the creation and components of entities. 
* `player` Reference to the player entity that is firing the projectile. The player's position and direction will be used to spawn the projectile.



**Returns:**

[**Vector2D**](classVector2D.md) The starting position of the newly spawned projectile.




**Note:**

The projectile may also include additional logic such as setting its velocity and direction based on the player's orientation or input.


Example usage: 
```C++
ShootSystem shootSystem;
Vector2D projectilePosition = shootSystem.spawn_projectile(registry,
playerEntity);
```
 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Shoot_system.hpp`

