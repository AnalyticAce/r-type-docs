

# File Entity.hpp



[**FileList**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Entity.hpp**](Entity_8hpp.md)

[Go to the source code of this file](Entity_8hpp_source.md)



* `#include <any>`
* `#include <cassert>`
* `#include <iostream>`
* `#include <memory>`
* `#include <mutex>`
* `#include <optional>`
* `#include <string>`
* `#include <typeindex>`
* `#include <unordered_map>`
* `#include <vector>`
* `#include "Vector.hpp"`















## Classes

| Type | Name |
| ---: | :--- |
| class | [**BBox**](classBBox.md) <br> |
| class | [**Entity**](classEntity.md) <br> |
| class | [**Health**](classHealth.md) <br> |
| class | [**Input**](classInput.md) <br> |
| class | [**Name**](className.md) <br> |
| class | [**Registry**](classRegistry.md) <br> |
| class | [**Score**](classScore.md) <br> |
| class | [**Transform**](classTransform.md) <br> |


## Public Types

| Type | Name |
| ---: | :--- |
| typedef std::map&lt; std::string, [**EntityVector**](Entity_8hpp.md#typedef-entityvector) &gt; | [**EntityMap**](#typedef-entitymap)  <br>_Map of entities by tag._  |
| typedef std::vector&lt; std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; &gt; | [**EntityVector**](#typedef-entityvector)  <br>_Vector of entities._  |
















































## Public Types Documentation




### typedef EntityMap 

```C++
typedef std::map<std::string, EntityVector> EntityMap;
```




<hr>



### typedef EntityVector 

```C++
typedef std::vector<std::shared_ptr<Entity> > EntityVector;
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Entity.hpp`

