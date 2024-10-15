

# Namespace protocol



[**Namespace List**](namespaces.md) **>** [**protocol**](namespaceprotocol.md)




















## Classes

| Type | Name |
| ---: | :--- |
| struct | [**EventNotification**](structprotocol_1_1EventNotification.md) <br>_Structure representing a notification about a game event._  |
| struct | [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) <br>_Structure representing an update to the game state._  |
| struct | [**PlayerAction**](structprotocol_1_1PlayerAction.md) <br>_Structure representing a player's action._  |


## Public Types

| Type | Name |
| ---: | :--- |
| enum uint8\_t | [**MessageType**](#enum-messagetype)  <br>_Enum class representing different types of messages exchanged between the client and server._  |




















## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**deserialize**](#function-deserialize) (const std::vector&lt; uint8\_t &gt; & buffer, [**PlayerAction**](structprotocol_1_1PlayerAction.md) & msg) <br>_Deserializes a byte buffer into a_ [_**PlayerAction**_](structprotocol_1_1PlayerAction.md) _message._ |
|  bool | [**deserialize**](#function-deserialize) (const std::vector&lt; uint8\_t &gt; & buffer, [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) & msg) <br>_Deserializes a byte buffer into a_ [_**GameStateUpdate**_](structprotocol_1_1GameStateUpdate.md) _message._ |
|  bool | [**deserialize**](#function-deserialize) (const std::vector&lt; uint8\_t &gt; & buffer, [**EventNotification**](structprotocol_1_1EventNotification.md) & msg) <br>_Deserializes a byte buffer into an_ [_**EventNotification**_](structprotocol_1_1EventNotification.md) _message._ |
|  std::vector&lt; uint8\_t &gt; | [**serialize**](#function-serialize) (const [**PlayerAction**](structprotocol_1_1PlayerAction.md) & msg) <br>_Serializes a_ [_**PlayerAction**_](structprotocol_1_1PlayerAction.md) _message into a byte vector._ |
|  std::vector&lt; uint8\_t &gt; | [**serialize**](#function-serialize) (const [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) & msg) <br>_Serializes a_ [_**GameStateUpdate**_](structprotocol_1_1GameStateUpdate.md) _message into a byte vector._ |
|  std::vector&lt; uint8\_t &gt; | [**serialize**](#function-serialize) (const [**EventNotification**](structprotocol_1_1EventNotification.md) & msg) <br>_Serializes an_ [_**EventNotification**_](structprotocol_1_1EventNotification.md) _message into a byte vector._ |




























## Public Types Documentation




### enum MessageType 

```C++
enum protocol::MessageType {
    PLAYER_ACTION = 1,
    GAME_STATE_UPDATE = 2,
    EVENT_NOTIFICATION = 3
};
```




<hr>
## Public Functions Documentation




### function deserialize 

_Deserializes a byte buffer into a_ [_**PlayerAction**_](structprotocol_1_1PlayerAction.md) _message._
```C++
bool protocol::deserialize (
    const std::vector< uint8_t > & buffer,
    PlayerAction & msg
) 
```





**Parameters:**


* `buffer` The byte vector containing the serialized data. 
* `msg` The [**PlayerAction**](structprotocol_1_1PlayerAction.md) message to populate with deserialized data. 



**Returns:**

true if deserialization was successful, false otherwise. 





        

<hr>



### function deserialize 

_Deserializes a byte buffer into a_ [_**GameStateUpdate**_](structprotocol_1_1GameStateUpdate.md) _message._
```C++
bool protocol::deserialize (
    const std::vector< uint8_t > & buffer,
    GameStateUpdate & msg
) 
```





**Parameters:**


* `buffer` The byte vector containing the serialized data. 
* `msg` The [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) message to populate with deserialized data. 



**Returns:**

true if deserialization was successful, false otherwise. 





        

<hr>



### function deserialize 

_Deserializes a byte buffer into an_ [_**EventNotification**_](structprotocol_1_1EventNotification.md) _message._
```C++
bool protocol::deserialize (
    const std::vector< uint8_t > & buffer,
    EventNotification & msg
) 
```





**Parameters:**


* `buffer` The byte vector containing the serialized data. 
* `msg` The [**EventNotification**](structprotocol_1_1EventNotification.md) message to populate with deserialized data. 



**Returns:**

true if deserialization was successful, false otherwise. 





        

<hr>



### function serialize 

_Serializes a_ [_**PlayerAction**_](structprotocol_1_1PlayerAction.md) _message into a byte vector._
```C++
std::vector< uint8_t > protocol::serialize (
    const PlayerAction & msg
) 
```





**Parameters:**


* `msg` The [**PlayerAction**](structprotocol_1_1PlayerAction.md) message to serialize. 



**Returns:**

A vector of bytes representing the serialized message. 





        

<hr>



### function serialize 

_Serializes a_ [_**GameStateUpdate**_](structprotocol_1_1GameStateUpdate.md) _message into a byte vector._
```C++
std::vector< uint8_t > protocol::serialize (
    const GameStateUpdate & msg
) 
```





**Parameters:**


* `msg` The [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) message to serialize. 



**Returns:**

A vector of bytes representing the serialized message. 





        

<hr>



### function serialize 

_Serializes an_ [_**EventNotification**_](structprotocol_1_1EventNotification.md) _message into a byte vector._
```C++
std::vector< uint8_t > protocol::serialize (
    const EventNotification & msg
) 
```





**Parameters:**


* `msg` The [**EventNotification**](structprotocol_1_1EventNotification.md) message to serialize. 



**Returns:**

A vector of bytes representing the serialized message. 





        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/protocol.hpp`

