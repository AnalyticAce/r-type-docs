

# Namespace protocol



[**Namespace List**](namespaces.md) **>** [**protocol**](namespaceprotocol.md)




















## Classes

| Type | Name |
| ---: | :--- |
| struct | [**EventNotification**](structprotocol_1_1EventNotification.md) <br> |
| struct | [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) <br> |
| struct | [**PlayerAction**](structprotocol_1_1PlayerAction.md) <br> |


## Public Types

| Type | Name |
| ---: | :--- |
| enum uint8\_t | [**MessageType**](#enum-messagetype)  <br> |




















## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**deserialize**](#function-deserialize) (const std::vector&lt; uint8\_t &gt; & buffer, [**PlayerAction**](structprotocol_1_1PlayerAction.md) & msg) <br> |
|  bool | [**deserialize**](#function-deserialize) (const std::vector&lt; uint8\_t &gt; & buffer, [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) & msg) <br> |
|  bool | [**deserialize**](#function-deserialize) (const std::vector&lt; uint8\_t &gt; & buffer, [**EventNotification**](structprotocol_1_1EventNotification.md) & msg) <br> |
|  std::vector&lt; uint8\_t &gt; | [**serialize**](#function-serialize) (const [**PlayerAction**](structprotocol_1_1PlayerAction.md) & msg) <br> |
|  std::vector&lt; uint8\_t &gt; | [**serialize**](#function-serialize) (const [**GameStateUpdate**](structprotocol_1_1GameStateUpdate.md) & msg) <br> |
|  std::vector&lt; uint8\_t &gt; | [**serialize**](#function-serialize) (const [**EventNotification**](structprotocol_1_1EventNotification.md) & msg) <br> |




























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

```C++
bool protocol::deserialize (
    const std::vector< uint8_t > & buffer,
    PlayerAction & msg
) 
```




<hr>



### function deserialize 

```C++
bool protocol::deserialize (
    const std::vector< uint8_t > & buffer,
    GameStateUpdate & msg
) 
```




<hr>



### function deserialize 

```C++
bool protocol::deserialize (
    const std::vector< uint8_t > & buffer,
    EventNotification & msg
) 
```




<hr>



### function serialize 

```C++
std::vector< uint8_t > protocol::serialize (
    const PlayerAction & msg
) 
```




<hr>



### function serialize 

```C++
std::vector< uint8_t > protocol::serialize (
    const GameStateUpdate & msg
) 
```




<hr>



### function serialize 

```C++
std::vector< uint8_t > protocol::serialize (
    const EventNotification & msg
) 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/include/protocol.hpp`

