

# Struct protocol::EventNotification



[**ClassList**](annotated.md) **>** [**protocol**](namespaceprotocol.md) **>** [**EventNotification**](structprotocol_1_1EventNotification.md)



_Structure representing a notification about a game event._ 

* `#include <protocol.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::vector&lt; uint8\_t &gt; | [**event\_data**](#variable-event_data)  <br>_Additional data related to the event._  |
|  uint8\_t | [**event\_type**](#variable-event_type)  <br>_Type of the event being notified._  |












































## Public Attributes Documentation




### variable event\_data 

```C++
std::vector<uint8_t> protocol::EventNotification::event_data;
```




<hr>



### variable event\_type 

```C++
uint8_t protocol::EventNotification::event_type;
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/protocol.hpp`

