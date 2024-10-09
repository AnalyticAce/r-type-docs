

# File Entity.hpp



[**FileList**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Entity.hpp**](Server_2include_2Entity_8hpp.md)

[Go to the source code of this file](Server_2include_2Entity_8hpp_source.md)



* `#include "Vector.hpp"`
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
| typedef std::map&lt; std::string, [**EntityVector**](GameLogic_2Entity_8hpp.md#typedef-entityvector) &gt; | [**EntityMap**](#typedef-entitymap)  <br> |
| typedef std::vector&lt; std::shared\_ptr&lt; [**Entity**](classEntity.md) &gt; &gt; | [**EntityVector**](#typedef-entityvector)  <br> |
















































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
The documentation for this class was generated from the following file `src/Server/include/Entity.hpp`

