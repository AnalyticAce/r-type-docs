

# Class Server



[**ClassList**](annotated.md) **>** [**Server**](classServer.md)





* `#include <Server.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::vector&lt; udp::endpoint &gt; | [**\_connected\_clients**](#variable-_connected_clients)  <br> |
|  boost::asio::steady\_timer | [**\_game\_time\_manager**](#variable-_game_time_manager)  <br> |
|  [**CollisionSystem**](classCollisionSystem.md) | [**collision**](#variable-collision)  <br> |
|  [**TimeManager**](classTimeManager.md) | [**enemyTimer**](#variable-enemytimer)  <br> |
|  u\_int16\_t | [**enemy\_count**](#variable-enemy_count)   = = 0<br> |
|  bool | [**game\_run**](#variable-game_run)   = = false<br> |
|  std::vector&lt; std::pair&lt; udp::endpoint, std::string &gt; &gt; | [**id\_name**](#variable-id_name)  <br> |
|  [**MouvementSystem**](classMouvementSystem.md) | [**movement**](#variable-movement)  <br> |
|  u\_int16\_t | [**players\_count**](#variable-players_count)   = = 0<br> |
|  [**Registry**](classRegistry.md) | [**registry**](#variable-registry)  <br> |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Server**](#function-server) (boost::asio::io\_context & io\_context, [**server\_t**](Server_8hpp.md#typedef-server_t) server\_me) <br> |
|  void | [**check\_player\_message**](#function-check_player_message) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br> |
|  void | [**check\_player\_position**](#function-check_player_position) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br> |
|  int | [**get\_player\_id**](#function-get_player_id) (const udp::endpoint & client\_endpoint) <br> |
|  void | [**handle\_client\_ping**](#function-handle_client_ping) (const udp::endpoint & client\_endpoint) <br> |
|  void | [**handle\_list\_rooms**](#function-handle_list_rooms) (udp::socket & socket, const udp::endpoint & client\_endpoint) <br> |
|  void | [**handle\_room\_creation**](#function-handle_room_creation) (udp::socket & socket, const std::string & room\_name, const udp::endpoint & client\_endpoint) <br> |
|  void | [**handle\_room\_joining**](#function-handle_room_joining) (udp::socket & socket, int room\_id, const udp::endpoint & client\_endpoint) <br> |
|  void | [**handle\_tcp\_connection**](#function-handle_tcp_connection) (boost::asio::io\_context & io\_context, tcp::socket socket) <br> |
|  void | [**notify\_clients\_of\_disconnection**](#function-notify_clients_of_disconnection) (boost::asio::io\_context & io\_context, const udp::endpoint & disconnected\_client) <br> |
|  void | [**process\_message**](#function-process_message) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br> |
|  void | [**process\_message\_contain**](#function-process_message_contain) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br> |
|  void | [**run\_game**](#function-run_game) () <br> |
|  void | [**send\_udp\_with\_ack**](#function-send_udp_with_ack) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & message, const udp::endpoint & client\_endpoint) <br> |
|  void | [**start\_heartbeat\_monitor**](#function-start_heartbeat_monitor) (boost::asio::io\_context & io\_context) <br> |
|  void | [**start\_tcp\_server**](#function-start_tcp_server) (boost::asio::io\_context & io\_context, int port) <br> |
|  void | [**start\_udp\_server**](#function-start_udp_server) (boost::asio::io\_context & io\_context, int port) <br> |
|   | [**~Server**](#function-server) () <br> |




























## Public Attributes Documentation




### variable \_connected\_clients 

```C++
std::vector<udp::endpoint> Server::_connected_clients;
```




<hr>



### variable \_game\_time\_manager 

```C++
boost::asio::steady_timer Server::_game_time_manager;
```




<hr>



### variable collision 

```C++
CollisionSystem Server::collision;
```




<hr>



### variable enemyTimer 

```C++
TimeManager Server::enemyTimer;
```




<hr>



### variable enemy\_count 

```C++
u_int16_t Server::enemy_count;
```




<hr>



### variable game\_run 

```C++
bool Server::game_run;
```




<hr>



### variable id\_name 

```C++
std::vector<std::pair<udp::endpoint, std::string> > Server::id_name;
```




<hr>



### variable movement 

```C++
MouvementSystem Server::movement;
```




<hr>



### variable players\_count 

```C++
u_int16_t Server::players_count;
```




<hr>



### variable registry 

```C++
Registry Server::registry;
```




<hr>
## Public Functions Documentation




### function Server 

```C++
Server::Server (
    boost::asio::io_context & io_context,
    server_t server_me
) 
```




<hr>



### function check\_player\_message 

```C++
void Server::check_player_message (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function check\_player\_position 

```C++
void Server::check_player_position (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function get\_player\_id 

```C++
int Server::get_player_id (
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function handle\_client\_ping 

```C++
void Server::handle_client_ping (
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function handle\_list\_rooms 

```C++
void Server::handle_list_rooms (
    udp::socket & socket,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function handle\_room\_creation 

```C++
void Server::handle_room_creation (
    udp::socket & socket,
    const std::string & room_name,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function handle\_room\_joining 

```C++
void Server::handle_room_joining (
    udp::socket & socket,
    int room_id,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function handle\_tcp\_connection 

```C++
void Server::handle_tcp_connection (
    boost::asio::io_context & io_context,
    tcp::socket socket
) 
```




<hr>



### function notify\_clients\_of\_disconnection 

```C++
void Server::notify_clients_of_disconnection (
    boost::asio::io_context & io_context,
    const udp::endpoint & disconnected_client
) 
```




<hr>



### function process\_message 

```C++
void Server::process_message (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function process\_message\_contain 

```C++
void Server::process_message_contain (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function run\_game 

```C++
void Server::run_game () 
```




<hr>



### function send\_udp\_with\_ack 

```C++
void Server::send_udp_with_ack (
    udp::socket & socket,
    const std::vector< uint8_t > & message,
    const udp::endpoint & client_endpoint
) 
```




<hr>



### function start\_heartbeat\_monitor 

```C++
void Server::start_heartbeat_monitor (
    boost::asio::io_context & io_context
) 
```




<hr>



### function start\_tcp\_server 

```C++
void Server::start_tcp_server (
    boost::asio::io_context & io_context,
    int port
) 
```




<hr>



### function start\_udp\_server 

```C++
void Server::start_udp_server (
    boost::asio::io_context & io_context,
    int port
) 
```




<hr>



### function ~Server 

```C++
Server::~Server () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/include/Server.hpp`

