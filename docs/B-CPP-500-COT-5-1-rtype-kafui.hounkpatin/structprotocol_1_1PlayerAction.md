

# Struct protocol::PlayerAction



[**ClassList**](annotated.md) **>** [**protocol**](namespaceprotocol.md) **>** [**PlayerAction**](structprotocol_1_1PlayerAction.md)



_Structure representing a player's action._ 

* `#include <protocol.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  uint8\_t | [**action\_type**](#variable-action_type)  <br>_Type of action performed by the player._  |
|  std::vector&lt; uint8\_t &gt; | [**data**](#variable-data)  <br>_Additional data related to the action._  |
|  uint32\_t | [**player\_id**](#variable-player_id)  <br>_Unique ID of the player performing the action._  |












































## Public Attributes Documentation




### variable action\_type 

```C++
uint8_t protocol::PlayerAction::action_type;
```




<hr>



### variable data 

```C++
std::vector<uint8_t> protocol::PlayerAction::data;
```




<hr>



### variable player\_id 

```C++
uint32_t protocol::PlayerAction::player_id;
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/protocol.hpp`

