

# File check\_params.cpp



[**FileList**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**check\_params.cpp**](check__params_8cpp.md)

[Go to the source code of this file](check__params_8cpp_source.md)



* `#include "../../include/Server/Server.hpp"`























## Public Static Attributes

| Type | Name |
| ---: | :--- |
|  const [**server\_t**](Server_8hpp.md#typedef-server_t) | [**CHECK\_SERVER**](#variable-check_server)   = = {.tcp\_port = -1, .udp\_port = -1}<br> |
|  const std::vector&lt; [**parameter\_t**](structparameter__t.md) &gt; | [**ZAPPY\_SERVER\_PARAMS**](#variable-zappy_server_params)   = = {
    {"-tcp", [](int \*param, char \*\*av) -&gt; bool { return [**sup\_int\_spec**](check__params_8cpp.md#function-sup_int_spec)(param, av); }, "tcp\_port",
     "is the tcp port number",
     static\_cast&lt;int&gt;(reinterpret\_cast&lt;const char \*&gt;(&CHECK\_SERVER.tcp\_port) -
                      reinterpret\_cast&lt;const char \*&gt;(&CHECK\_SERVER))},
    {"-udp", [](int \*param, char \*\*av) -&gt; bool { return [**sup\_int\_spec**](check__params_8cpp.md#function-sup_int_spec)(param, av); }, "udp\_port",
     "is the udp port number",
     static\_cast&lt;int&gt;(reinterpret\_cast&lt;const char \*&gt;(&CHECK\_SERVER.udp\_port) -
                      reinterpret\_cast&lt;const char \*&gt;(&CHECK\_SERVER))}}<br> |














## Public Functions

| Type | Name |
| ---: | :--- |
|  bool | [**add\_to\_server\_struct**](#function-add_to_server_struct) ([**server\_t**](Server_8hpp.md#typedef-server_t) \* server, char \*\* av, int i) <br> |
|  void | [**initialize\_parameters**](#function-initialize_parameters) ([**server\_t**](Server_8hpp.md#typedef-server_t) \* server) <br> |
|  bool | [**recup\_args**](#function-recup_args) ([**server\_t**](Server_8hpp.md#typedef-server_t) \* server, int ac, char \*\* av) <br> |
|  bool | [**sup\_int\_spec**](#function-sup_int_spec) (int \* param, char \*\* av) <br> |
|  void | [**usage**](#function-usage) () <br> |




























## Public Static Attributes Documentation




### variable CHECK\_SERVER 

```C++
const server_t CHECK_SERVER;
```




<hr>



### variable ZAPPY\_SERVER\_PARAMS 

```C++
const std::vector<parameter_t> ZAPPY_SERVER_PARAMS;
```




<hr>
## Public Functions Documentation




### function add\_to\_server\_struct 

```C++
bool add_to_server_struct (
    server_t * server,
    char ** av,
    int i
) 
```




<hr>



### function initialize\_parameters 

```C++
void initialize_parameters (
    server_t * server
) 
```




<hr>



### function recup\_args 

```C++
bool recup_args (
    server_t * server,
    int ac,
    char ** av
) 
```




<hr>



### function sup\_int\_spec 

```C++
bool sup_int_spec (
    int * param,
    char ** av
) 
```




<hr>



### function usage 

```C++
void usage () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/check_params.cpp`

