

# Class Registry



[**ClassList**](annotated.md) **>** [**Registry**](classRegistry.md)





* `#include <Entity.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Registry**](#function-registry-12) () <br> |
|   | [**Registry**](#function-registry-12) () <br> |
|  std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; | [**add\_entity**](#function-add_entity-12) (const std::string tag) <br> |
|  std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; | [**add\_entity**](#function-add_entity-12) (const std::string tag) <br> |
|  void | [**entity\_update**](#function-entity_update-12) () <br> |
|  void | [**entity\_update**](#function-entity_update-12) () <br> |
|  [**EntityVector**](Server_2include_2Entity_8hpp.md#typedef-entityvector) & | [**get\_entities**](#function-get_entities-14) (const std::string tag) <br> |
|  [**EntityVector**](Server_2include_2Entity_8hpp.md#typedef-entityvector) & | [**get\_entities**](#function-get_entities-24) () <br> |
|  [**EntityVector**](Server_2include_2Entity_8hpp.md#typedef-entityvector) & | [**get\_entities**](#function-get_entities-14) (const std::string tag) <br> |
|  [**EntityVector**](Server_2include_2Entity_8hpp.md#typedef-entityvector) & | [**get\_entities**](#function-get_entities-24) () <br> |
|  void | [**remove\_entity**](#function-remove_entity-12) (const size\_t id) <br> |
|  void | [**remove\_entity**](#function-remove_entity-12) (const size\_t id) <br> |
|  void | [**spawn\_coin**](#function-spawn_coin-12) () <br> |
|  void | [**spawn\_coin**](#function-spawn_coin-12) () <br> |
|  void | [**spawn\_enemy**](#function-spawn_enemy-12) () <br> |
|  [**Vector2D**](classVector2D.md) | [**spawn\_enemy**](#function-spawn_enemy-12) () <br> |
|  void | [**spawn\_player**](#function-spawn_player-12) (std::string name) <br> |
|  void | [**spawn\_player**](#function-spawn_player-12) (std::string name) <br> |




























## Public Functions Documentation




### function Registry [1/2]

```C++
inline Registry::Registry () 
```




<hr>



### function Registry [1/2]

```C++
inline Registry::Registry () 
```




<hr>



### function add\_entity [1/2]

```C++
std::shared_ptr< Entity > Registry::add_entity (
    const std::string tag
) 
```




<hr>



### function add\_entity [1/2]

```C++
std::shared_ptr< Entity > Registry::add_entity (
    const std::string tag
) 
```




<hr>



### function entity\_update [1/2]

```C++
void Registry::entity_update () 
```




<hr>



### function entity\_update [1/2]

```C++
void Registry::entity_update () 
```




<hr>



### function get\_entities [1/4]

```C++
EntityVector & Registry::get_entities (
    const std::string tag
) 
```




<hr>



### function get\_entities [2/4]

```C++
EntityVector & Registry::get_entities () 
```




<hr>



### function get\_entities [1/4]

```C++
EntityVector & Registry::get_entities (
    const std::string tag
) 
```




<hr>



### function get\_entities [2/4]

```C++
EntityVector & Registry::get_entities () 
```




<hr>



### function remove\_entity [1/2]

```C++
void Registry::remove_entity (
    const size_t id
) 
```




<hr>



### function remove\_entity [1/2]

```C++
void Registry::remove_entity (
    const size_t id
) 
```




<hr>



### function spawn\_coin [1/2]

```C++
void Registry::spawn_coin () 
```




<hr>



### function spawn\_coin [1/2]

```C++
void Registry::spawn_coin () 
```




<hr>



### function spawn\_enemy [1/2]

```C++
void Registry::spawn_enemy () 
```




<hr>



### function spawn\_enemy [1/2]

```C++
Vector2D Registry::spawn_enemy () 
```




<hr>



### function spawn\_player [1/2]

```C++
void Registry::spawn_player (
    std::string name
) 
```




<hr>



### function spawn\_player [1/2]

```C++
void Registry::spawn_player (
    std::string name
) 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/GameLogic/Entity.hpp`

