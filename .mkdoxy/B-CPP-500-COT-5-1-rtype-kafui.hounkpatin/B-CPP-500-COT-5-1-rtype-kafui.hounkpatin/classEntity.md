

# Class Entity



[**ClassList**](annotated.md) **>** [**Entity**](classEntity.md)





* `#include <Entity.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  bool | [**\_alive**](#variable-_alive)   = = true<br> |
|  const size\_t | [**\_id**](#variable-_id)   = = 0<br> |
|  const std::string | [**\_tag**](#variable-_tag)   = = "Default"<br> |
|  std::unique\_ptr&lt; [**BBox**](classBBox.md) &gt; | [**bbox**](#variable-bbox)  <br> |
|  std::unique\_ptr&lt; [**CirShape**](classCirShape.md) &gt; | [**cirshape**](#variable-cirshape)  <br> |
|  std::unique\_ptr&lt; [**Health**](classHealth.md) &gt; | [**health**](#variable-health)  <br> |
|  std::unique\_ptr&lt; [**Input**](classInput.md) &gt; | [**input**](#variable-input)  <br> |
|  std::unique\_ptr&lt; [**Name**](className.md) &gt; | [**name**](#variable-name)  <br> |
|  std::unique\_ptr&lt; [**RectShape**](classRectShape.md) &gt; | [**rectshape**](#variable-rectshape)  <br> |
|  std::unique\_ptr&lt; [**Score**](classScore.md) &gt; | [**score**](#variable-score)  <br> |
|  std::unique\_ptr&lt; [**Transform**](classTransform.md) &gt; | [**transform**](#variable-transform)  <br> |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Entity**](#function-entity-14) () <br> |
|   | [**Entity**](#function-entity-24) (size\_t id, std::string tag) <br> |
|   | [**Entity**](#function-entity-14) () <br> |
|   | [**Entity**](#function-entity-24) (size\_t id, std::string tag) <br> |
|  void | [**destroy**](#function-destroy-12) () <br> |
|  void | [**destroy**](#function-destroy-12) () <br> |




























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
std::unique_ptr< BBox > Entity::bbox;
```




<hr>



### variable cirshape 

```C++
std::unique_ptr<CirShape> Entity::cirshape;
```




<hr>



### variable health 

```C++
std::unique_ptr< Health > Entity::health;
```




<hr>



### variable input 

```C++
std::unique_ptr< Input > Entity::input;
```




<hr>



### variable name 

```C++
std::unique_ptr< Name > Entity::name;
```




<hr>



### variable rectshape 

```C++
std::unique_ptr<RectShape> Entity::rectshape;
```




<hr>



### variable score 

```C++
std::unique_ptr< Score > Entity::score;
```




<hr>



### variable transform 

```C++
std::unique_ptr< Transform > Entity::transform;
```




<hr>
## Public Functions Documentation




### function Entity [1/4]

```C++
inline Entity::Entity () 
```




<hr>



### function Entity [2/4]

```C++
inline Entity::Entity (
    size_t id,
    std::string tag
) 
```




<hr>



### function Entity [1/4]

```C++
inline Entity::Entity () 
```




<hr>



### function Entity [2/4]

```C++
inline Entity::Entity (
    size_t id,
    std::string tag
) 
```




<hr>



### function destroy [1/2]

```C++
inline void Entity::destroy () 
```




<hr>



### function destroy [1/2]

```C++
inline void Entity::destroy () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/GameLogic/Entity.hpp`

