

# Class Entity



[**ClassList**](annotated.md) **>** [**Entity**](classEntity.md)



_Represents a game object composed of multiple components._ [More...](#detailed-description)

* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  bool | [**\_alive**](#variable-_alive)   = = true<br>_Whether the entity is active or destroyed._  |
|  const size\_t | [**\_id**](#variable-_id)  <br>_Unique identifier of the entity._  |
|  const std::string | [**\_tag**](#variable-_tag)  <br>_Tag representing the entity's type._  |
|  std::unique\_ptr&lt; [**BBox**](classBBox.md) &gt; | [**bbox**](#variable-bbox)  <br>_Bounding box component._  |
|  std::unique\_ptr&lt; [**Health**](classHealth.md) &gt; | [**health**](#variable-health)  <br>[_**Health**_](classHealth.md) _component._ |
|  std::unique\_ptr&lt; [**Input**](classInput.md) &gt; | [**input**](#variable-input)  <br>[_**Input**_](classInput.md) _component._ |
|  std::unique\_ptr&lt; [**Name**](className.md) &gt; | [**name**](#variable-name)  <br>[_**Name**_](className.md) _component._ |
|  std::unique\_ptr&lt; [**Score**](classScore.md) &gt; | [**score**](#variable-score)  <br>[_**Score**_](classScore.md) _component._ |
|  std::unique\_ptr&lt; [**Transform**](classTransform.md) &gt; | [**transform**](#variable-transform)  <br>[_**Transform**_](classTransform.md) _component._ |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Entity**](#function-entity) (size\_t id, std::string tag) <br>_Constructs an entity with a given ID and tag._  |
|  void | [**destroy**](#function-destroy) () <br>_Marks the entity as destroyed._  |




























# Detailed Description


Entities serve as building blocks for all game objects. They contain components such as position, health, and input to define their behavior and state. 


    
## Public Attributes Documentation




### variable \_alive 

```C++
bool Entity::_alive;
```




<hr>



### variable \_id 

```C++
const size_t Entity::_id;
```




<hr>



### variable \_tag 

```C++
const std::string Entity::_tag;
```




<hr>



### variable bbox 

```C++
std::unique_ptr<BBox> Entity::bbox;
```




<hr>



### variable health 

```C++
std::unique_ptr<Health> Entity::health;
```




<hr>



### variable input 

```C++
std::unique_ptr<Input> Entity::input;
```




<hr>



### variable name 

```C++
std::unique_ptr<Name> Entity::name;
```




<hr>



### variable score 

```C++
std::unique_ptr<Score> Entity::score;
```




<hr>



### variable transform 

```C++
std::unique_ptr<Transform> Entity::transform;
```




<hr>
## Public Functions Documentation




### function Entity 

_Constructs an entity with a given ID and tag._ 
```C++
inline Entity::Entity (
    size_t id,
    std::string tag
) 
```





**Parameters:**


* `id` The unique ID of the entity. 
* `tag` The tag representing the type of entity. 




        

<hr>



### function destroy 

```C++
inline void Entity::destroy () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

