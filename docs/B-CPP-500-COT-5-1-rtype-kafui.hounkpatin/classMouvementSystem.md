

# Class MouvementSystem



[**ClassList**](annotated.md) **>** [**MouvementSystem**](classMouvementSystem.md)



_Forward declaration of the_ [_**Registry**_](classRegistry.md) _class._[More...](#detailed-description)

* `#include <Mouvement_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**MouvementSystem**](#function-mouvementsystem) () <br>_Default constructor._  |
|  [**Vector2D**](classVector2D.md) | [**enemy\_move**](#function-enemy_move) ([**Registry**](classRegistry.md) & registry) <br>_Moves enemy entities and returns the new position._  |
|  void | [**handleInput**](#function-handleinput) ([**Registry**](classRegistry.md) & registry, std::string move\_direction, std::string name) <br>_Processes player input to trigger movement in a specific direction._  |
|  [**Vector2D**](classVector2D.md) | [**move\_player**](#function-move_player) ([**Registry**](classRegistry.md) & registry, std::string name) <br>_Moves a player based on their input and updates their position._  |
|  void | [**system\_movement**](#function-system_movement) (EntityVector & entities) <br>_Applies movement logic to a vector of entities._  |
|   | [**~MouvementSystem**](#function-mouvementsystem) () <br>_Destructor._  |




























# Detailed Description


The [**MouvementSystem**](classMouvementSystem.md) class handles all movement logic for players, enemies, and other entities in the game. 


    
## Public Functions Documentation




### function MouvementSystem 

```C++
inline MouvementSystem::MouvementSystem () 
```




<hr>



### function enemy\_move 

_Moves enemy entities and returns the new position._ 
```C++
Vector2D MouvementSystem::enemy_move (
    Registry & registry
) 
```



This method handles logic for enemy movement, potentially including AI behavior.




**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) containing all entities. 



**Returns:**

The new position of the enemy as a [**Vector2D**](classVector2D.md). 





        

<hr>



### function handleInput 

_Processes player input to trigger movement in a specific direction._ 
```C++
void MouvementSystem::handleInput (
    Registry & registry,
    std::string move_direction,
    std::string name
) 
```





**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) containing all entities. 
* `move_direction` The direction of movement ("up", "down", "left", or "right"). 
* `name` The name of the player whose movement is being handled. 




        

<hr>



### function move\_player 

_Moves a player based on their input and updates their position._ 
```C++
Vector2D MouvementSystem::move_player (
    Registry & registry,
    std::string name
) 
```





**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) containing all entities. 
* `name` The name of the player to move. 



**Returns:**

The updated position of the player as a [**Vector2D**](classVector2D.md). 





        

<hr>



### function system\_movement 

_Applies movement logic to a vector of entities._ 
```C++
void MouvementSystem::system_movement (
    EntityVector & entities
) 
```



This method iterates through a list of entities, updating their positions based on their velocity and other factors.




**Parameters:**


* `entities` A reference to the vector of entities to process. 




        

<hr>



### function ~MouvementSystem 

```C++
inline MouvementSystem::~MouvementSystem () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Mouvement_system.hpp`

