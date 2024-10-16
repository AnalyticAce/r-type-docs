

# Class CoinSystem



[**ClassList**](annotated.md) **>** [**CoinSystem**](classCoinSystem.md)



_Manages the logic related to coins within the ECS (_ [_**Entity**_](classEntity.md) _Component System)._[More...](#detailed-description)

* `#include <Coin_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|  void | [**checkCoins**](#function-checkcoins) ([**Registry**](classRegistry.md) & registry) <br>_Checks and updates the status of coins for entities in the registry._  |




























# Detailed Description


The [**CoinSystem**](classCoinSystem.md) class contains methods responsible for verifying and processing coin-related aspects for entities managed by the ECS. This is a system class that interacts with the entity registry to apply logic to components. 


    
## Public Functions Documentation




### function checkCoins 

_Checks and updates the status of coins for entities in the registry._ 
```C++
void CoinSystem::checkCoins (
    Registry & registry
) 
```



This method loops through the relevant entities in the provided registry and applies the coin-related logic, such as updating coin counts, triggering rewards, or handling coin collection events.




**Parameters:**


* `registry` Reference to the [**Registry**](classRegistry.md) object that holds all the entities and their components. This allows the [**CoinSystem**](classCoinSystem.md) to access and modify the state of entities related to coins. 




        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Coin_system.hpp`

