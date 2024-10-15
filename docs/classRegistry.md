

# Class Registry



[**ClassList**](annotated.md) **>** [**Registry**](classRegistry.md)





* `#include <Entity.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Registry**](#function-registry) () <br>_Default constructor._  |
|  std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; | [**add\_entity**](#function-add_entity) (const std::string tag) <br> |
|  void | [**entity\_update**](#function-entity_update) () <br>_Updates all entities in the registry._  |
|  [**EntityVector**](Entity_8hpp.md#typedef-entityvector) & | [**get\_entities**](#function-get_entities-12) (const std::string tag) <br> |
|  [**EntityVector**](Entity_8hpp.md#typedef-entityvector) & | [**get\_entities**](#function-get_entities-22) () <br> |
|  void | [**remove\_entity**](#function-remove_entity) (const size\_t id) <br> |
|  void | [**spawn\_boss**](#function-spawn_boss) () <br>_Spawns a boss entity in the game._  |
|  void | [**spawn\_coin**](#function-spawn_coin) () <br>_Spawns a coin entity in the game._  |
|  [**Vector2D**](classVector2D.md) | [**spawn\_enemy**](#function-spawn_enemy) () <br> |
|  void | [**spawn\_player**](#function-spawn_player) (std::string name) <br> |




























## Public Functions Documentation




### function Registry 

```C++
inline Registry::Registry () 
```




<hr>



### function add\_entity 


```C++
std::shared_ptr< Entity > Registry::add_entity (
    const std::string tag
) 
```



Adds a new entity with the given tag. 

**Parameters:**


* `tag` The tag identifying the type of entity. 



**Returns:**

A shared pointer to the newly created entity. 





        

<hr>



### function entity\_update 

```C++
void Registry::entity_update () 
```




<hr>



### function get\_entities [1/2]


```C++
EntityVector & Registry::get_entities (
    const std::string tag
) 
```



Retrieves a reference to the vector of entities with the given tag. 

**Parameters:**


* `tag` The tag identifying the type of entities to retrieve. 



**Returns:**

Reference to the vector of entities with the specified tag. 





        

<hr>



### function get\_entities [2/2]


```C++
EntityVector & Registry::get_entities () 
```



Retrieves a reference to the vector of all entities. 

**Returns:**

Reference to the vector of all active entities. 





        

<hr>



### function remove\_entity 


```C++
void Registry::remove_entity (
    const size_t id
) 
```



Removes an entity with the given ID from the registry. 

**Parameters:**


* `id` The unique ID of the entity to remove. 




        

<hr>



### function spawn\_boss 

```C++
void Registry::spawn_boss () 
```




<hr>



### function spawn\_coin 

```C++
void Registry::spawn_coin () 
```




<hr>



### function spawn\_enemy 


```C++
Vector2D Registry::spawn_enemy () 
```



Spawns an enemy entity and returns its initial position. 

**Returns:**

The initial position of the spawned enemy. 





        

<hr>



### function spawn\_player 


```C++
void Registry::spawn_player (
    std::string name
) 
```



Spawns a player entity with the given name. 

**Parameters:**


* `name` The name of the player. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

