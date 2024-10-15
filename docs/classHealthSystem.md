

# Class HealthSystem



[**ClassList**](annotated.md) **>** [**HealthSystem**](classHealthSystem.md)



_Forward declaration of the_ [_**Registry**_](classRegistry.md) _class._[More...](#detailed-description)

* `#include <Health_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  void | [**checkHealth**](#function-checkhealth) ([**Registry**](classRegistry.md) & registry) <br>_Checks and updates the health status of entities in the registry._  |




























# Detailed Description


The [**HealthSystem**](classHealthSystem.md) class handles the logic related to the health status of entities within the game. 


    
## Public Functions Documentation




### function checkHealth 

_Checks and updates the health status of entities in the registry._ 
```C++
void HealthSystem::checkHealth (
    Registry & registry
) 
```



This function iterates through relevant entities and performs health-related operations, such as verifying if the entities are still alive, applying health changes, or marking entities for removal if their health reaches zero.




**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) instance containing the entities to process. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Health_system.hpp`

