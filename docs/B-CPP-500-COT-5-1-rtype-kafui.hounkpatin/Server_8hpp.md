

# File Server.hpp



[**FileList**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Server.hpp**](Server_8hpp.md)

[Go to the source code of this file](Server_8hpp_source.md)



* `#include <array>`
* `#include <boost/asio.hpp>`
* `#include <boost/bind/bind.hpp>`
* `#include <chrono>`
* `#include <cstring>`
* `#include <functional>`
* `#include <iostream>`
* `#include <string>`
* `#include <string_view>`
* `#include <thread>`
* `#include <unordered_map>`
* `#include <vector>`
* `#include "Coin_system.hpp"`
* `#include "Collision_system.hpp"`
* `#include "Entity.hpp"`
* `#include "Health_system.hpp"`
* `#include "Mouvement_system.hpp"`
* `#include "Shoot_system.hpp"`
* `#include "ThreadPool.hpp"`
* `#include "Time_manager.hpp"`
* `#include "protocol.hpp"`
* `#include "room_system.hpp"`















## Classes

| Type | Name |
| ---: | :--- |
| struct | [**EndpointEqual**](structEndpointEqual.md) <br>_Comparator for UDP endpoints._  |
| struct | [**EndpointHash**](structEndpointHash.md) <br>_Hash function for UDP endpoints._  |
| class | [**Server**](classServer.md) <br>_A class representing the server managing TCP/UDP connections and game state._  |
| struct | [**parameter\_t**](structparameter__t.md) <br>_Structure representing a command-line parameter._  |
| struct | [**server\_me\_t**](structserver__me__t.md) <br>_Struct representing the server configuration._  |


## Public Types

| Type | Name |
| ---: | :--- |
| typedef struct [**server\_me\_t**](structserver__me__t.md) | [**server\_t**](#typedef-server_t)  <br>_Struct representing the server configuration._  |




















## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**recup\_args**](#function-recup_args) ([**server\_t**](Server_8hpp.md#typedef-server_t) \* server, int ac, char \*\* av) <br> |




























## Public Types Documentation




### typedef server\_t 

_Struct representing the server configuration._ 
```C++
typedef struct server_me_t server_t;
```



This structure holds the port numbers for both TCP and UDP communication. 


        

<hr>
## Public Functions Documentation




### function recup\_args 

```C++
bool recup_args (
    server_t * server,
    int ac,
    char ** av
) 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Server.hpp`

