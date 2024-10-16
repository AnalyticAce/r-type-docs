

# Class Registry



[**ClassList**](annotated.md) **>** [**Registry**](classRegistry.md)



_Manages all entities in the game and their lifecycle._ [More...](#detailed-description)

* `#include <Entity.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; | [**add\_entity**](#function-add_entity) (const std::string tag) <br>_Adds a new entity with the given tag._  |
|  EntityVector & | [**get\_entities**](#function-get_entities) (const std::string tag) <br>_Retrieves entities by tag._  |
|  void | [**remove\_entity**](#function-remove_entity) (const size\_t id) <br>_Removes an entity from the registry by ID._  |




























# Detailed Description


The registry is responsible for creating, updating, and removing entities. It provides mechanisms to access entities by tag or ID and spawn new ones dynamically. 


    
## Public Functions Documentation




### function add\_entity 

_Adds a new entity with the given tag._ 
```C++
std::shared_ptr< Entity > Registry::add_entity (
    const std::string tag
) 
```





**Parameters:**


* `tag` The tag representing the entity type. 



**Returns:**

A shared pointer to the newly created entity. 





        

<hr>



### function get\_entities 

_Retrieves entities by tag._ 
```C++
EntityVector & Registry::get_entities (
    const std::string tag
) 
```





**Parameters:**


* `tag` The tag to filter entities. 



**Returns:**

Reference to the vector of entities matching the tag. 





        

<hr>



### function remove\_entity 

_Removes an entity from the registry by ID._ 
```C++
void Registry::remove_entity (
    const size_t id
) 
```





**Parameters:**


* `id` The unique ID of the entity to remove. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

