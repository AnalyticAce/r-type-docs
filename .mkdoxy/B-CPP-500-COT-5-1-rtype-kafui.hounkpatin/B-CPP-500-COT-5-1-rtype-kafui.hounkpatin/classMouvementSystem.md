

# Class MouvementSystem



[**ClassList**](annotated.md) **>** [**MouvementSystem**](classMouvementSystem.md)





* `#include <Mouvement_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**MouvementSystem**](#function-mouvementsystem-12) () <br> |
|   | [**MouvementSystem**](#function-mouvementsystem-12) () <br> |
|  [**Vector2D**](classVector2D.md) | [**enemy\_move**](#function-enemy_move) ([**Registry**](classRegistry.md) & registry) <br> |
|  void | [**handleInput**](#function-handleinput-12) ([**Input**](classInput.md) & input) <br> |
|  void | [**handleInput**](#function-handleinput-22) ([**Registry**](classRegistry.md) & registry, std::string move\_direction, std::string name) <br> |
|  void | [**move\_player**](#function-move_player-12) ([**Registry**](classRegistry.md) & registry, std::string name) <br> |
|  [**Vector2D**](classVector2D.md) | [**move\_player**](#function-move_player-12) ([**Registry**](classRegistry.md) & registry, std::string name) <br> |
|  void | [**system\_movement**](#function-system_movement-12) ([**EntityVector**](GameLogic_2Entity_8hpp.md#typedef-entityvector) & entities) <br> |
|  void | [**system\_movement**](#function-system_movement-12) ([**EntityVector**](GameLogic_2Entity_8hpp.md#typedef-entityvector) & entities) <br> |
|   | [**~MouvementSystem**](#function-mouvementsystem-12) () <br> |
|   | [**~MouvementSystem**](#function-mouvementsystem-12) () <br> |




























## Public Functions Documentation




### function MouvementSystem [1/2]

```C++
inline MouvementSystem::MouvementSystem () 
```




<hr>



### function MouvementSystem [1/2]

```C++
inline MouvementSystem::MouvementSystem () 
```




<hr>



### function enemy\_move 

```C++
Vector2D MouvementSystem::enemy_move (
    Registry & registry
) 
```




<hr>



### function handleInput [1/2]

```C++
void MouvementSystem::handleInput (
    Input & input
) 
```




<hr>



### function handleInput [2/2]

```C++
void MouvementSystem::handleInput (
    Registry & registry,
    std::string move_direction,
    std::string name
) 
```




<hr>



### function move\_player [1/2]

```C++
void MouvementSystem::move_player (
    Registry & registry,
    std::string name
) 
```




<hr>



### function move\_player [1/2]

```C++
Vector2D MouvementSystem::move_player (
    Registry & registry,
    std::string name
) 
```




<hr>



### function system\_movement [1/2]

```C++
void MouvementSystem::system_movement (
    EntityVector & entities
) 
```




<hr>



### function system\_movement [1/2]

```C++
void MouvementSystem::system_movement (
    EntityVector & entities
) 
```




<hr>



### function ~MouvementSystem [1/2]

```C++
inline MouvementSystem::~MouvementSystem () 
```




<hr>



### function ~MouvementSystem [1/2]

```C++
inline MouvementSystem::~MouvementSystem () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/GameLogic/Mouvement_system.hpp`

