

# File Server.hpp



[**FileList**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Server.hpp**](Server_8hpp.md)

[Go to the source code of this file](Server_8hpp_source.md)



* `#include "../include/protocol.hpp"`
* `#include "ThreadPool.hpp"`
* `#include "room_system.hpp"`
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
* `#include "Time_manager.hpp"`















## Classes

| Type | Name |
| ---: | :--- |
| struct | [**EndpointEqual**](structEndpointEqual.md) <br> |
| struct | [**EndpointHash**](structEndpointHash.md) <br> |
| class | [**Server**](classServer.md) <br> |
| struct | [**parameter\_t**](structparameter__t.md) <br> |
| struct | [**server\_me\_t**](structserver__me__t.md) <br> |


## Public Types

| Type | Name |
| ---: | :--- |
| typedef struct [**server\_me\_t**](structserver__me__t.md) | [**server\_t**](#typedef-server_t)  <br> |




















## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**recup\_args**](#function-recup_args) ([**server\_t**](Server_8hpp.md#typedef-server_t) \* server, int ac, char \*\* av) <br> |




























## Public Types Documentation




### typedef server\_t 

```C++
typedef struct server_me_t server_t;
```




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
The documentation for this class was generated from the following file `src/Server/include/Server.hpp`

