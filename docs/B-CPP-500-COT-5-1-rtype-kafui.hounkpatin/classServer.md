

# Class Server



[**ClassList**](annotated.md) **>** [**Server**](classServer.md)



_A class representing the server managing TCP/UDP connections and game state._ [More...](#detailed-description)

* `#include <Server.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::vector&lt; udp::endpoint &gt; | [**\_connected\_clients**](#variable-_connected_clients)  <br>_A list of connected clients._  |
|  boost::asio::steady\_timer | [**\_game\_time\_manager**](#variable-_game_time_manager)  <br>_Timer to manage game-related events._  |
|  std::string | [**\_name**](#variable-_name)  <br>_The name of the player._  |
|  [**TimeManager**](classTimeManager.md) | [**coinTimer**](#variable-cointimer)  <br>_Timer to manage coin spawning._  |
|  u\_int16\_t | [**coin\_count**](#variable-coin_count)   = = 0<br>_Number of active coins._  |
|  [**CollisionSystem**](classCollisionSystem.md) | [**collision**](#variable-collision)  <br>_System to handle collision detection._  |
|  [**TimeManager**](classTimeManager.md) | [**enemyTimer**](#variable-enemytimer)  <br>_Timer to manage enemy spawning and actions._  |
|  u\_int16\_t | [**enemy\_count**](#variable-enemy_count)   = = 0<br>_Number of active enemies._  |
|  bool | [**game\_run**](#variable-game_run)   = = false<br>_Flag to track if the game is running._  |
|  std::vector&lt; std::pair&lt; udp::endpoint, std::string &gt; &gt; | [**id\_name**](#variable-id_name)  <br>_A vector of connected client IDs and their names._  |
|  [**MouvementSystem**](classMouvementSystem.md) | [**movement**](#variable-movement)  <br>_System to handle player and object movement._  |
|  u\_int16\_t | [**players\_count**](#variable-players_count)   = = 0<br>_Number of connected players._  |
|  u\_int16\_t | [**projectile\_count**](#variable-projectile_count)   = = 0<br>_Number of active projectiles._  |
|  [**Registry**](classRegistry.md) | [**registry**](#variable-registry)  <br>[_**Registry**_](classRegistry.md) _to manage entities and components._ |
|  [**ShootSystem**](classShootSystem.md) | [**shoot**](#variable-shoot)  <br>_System to handle projectile shooting._  |
|  [**TimeManager**](classTimeManager.md) | [**shootTimer**](#variable-shoottimer)  <br>_Timer to manage shooting actions._  |
|  [**TimeManager**](classTimeManager.md) | [**updateTimer**](#variable-updatetimer)  <br>_Timer to manage game updates._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Server**](#function-server) (boost::asio::io\_context & io\_context, [**server\_t**](Server_8hpp.md#typedef-server_t) server\_me) <br>_Constructs a new_ [_**Server**_](classServer.md) _object._ |
|  void | [**check\_player\_message**](#function-check_player_message) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br>_Verifies and processes a player's incoming message._  |
|  void | [**check\_player\_position**](#function-check_player_position) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br>_Checks and updates the player's position._  |
|  [**Entity**](classEntity.md) & | [**get\_player\_entity**](#function-get_player_entity) (const std::string & player\_name) <br>_Retrieves the entity representing the player based on their name._  |
|  int | [**get\_player\_id**](#function-get_player_id) (const udp::endpoint & client\_endpoint) <br>_Retrieves the player's ID based on their endpoint._  |
|  std::string | [**get\_player\_name**](#function-get_player_name) (const udp::endpoint & client\_endpoint) <br>_Retrieves the player's name based on their endpoint._  |
|  void | [**handle\_client\_ping**](#function-handle_client_ping) (const udp::endpoint & client\_endpoint) <br>_Handles a ping message from a client to update the last communication time._  |
|  void | [**handle\_list\_rooms**](#function-handle_list_rooms) (udp::socket & socket, const udp::endpoint & client\_endpoint) <br>_Handles a client's request to list all available rooms._  |
|  void | [**handle\_room\_creation**](#function-handle_room_creation) (udp::socket & socket, const std::string & room\_name, const udp::endpoint & client\_endpoint) <br>_Handles the creation of a new room._  |
|  void | [**handle\_room\_joining**](#function-handle_room_joining) (udp::socket & socket, int room\_id, const udp::endpoint & client\_endpoint) <br>_Handles a client's request to join an existing room._  |
|  void | [**handle\_tcp\_connection**](#function-handle_tcp_connection) (boost::asio::io\_context & io\_context, tcp::socket socket) <br>_Handles a new TCP connection from a client._  |
|  void | [**notify\_clients\_of\_disconnection**](#function-notify_clients_of_disconnection) (boost::asio::io\_context & io\_context, const udp::endpoint & disconnected\_client) <br>_Notifies all connected clients about a client's disconnection._  |
|  void | [**process\_message**](#function-process_message) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br>_Processes an incoming UDP message from a client._  |
|  void | [**process\_message\_contain**](#function-process_message_contain) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & buffer, const udp::endpoint & client\_endpoint) <br>_Processes messages containing specific game data from a client._  |
|  void | [**run\_game**](#function-run_game) () <br>_Runs the main game loop._  |
|  void | [**send\_udp\_with\_ack**](#function-send_udp_with_ack) (udp::socket & socket, const std::vector&lt; uint8\_t &gt; & message, const udp::endpoint & client\_endpoint) <br>_Sends a UDP message to a client with acknowledgment support._  |
|  void | [**start\_heartbeat\_monitor**](#function-start_heartbeat_monitor) (boost::asio::io\_context & io\_context) <br>_Starts monitoring the heartbeat of connected clients._  |
|  void | [**start\_tcp\_server**](#function-start_tcp_server) (boost::asio::io\_context & io\_context, int port) <br>_Starts the TCP server on a given port._  |
|  void | [**start\_udp\_server**](#function-start_udp_server) (boost::asio::io\_context & io\_context, int port) <br>_Starts the UDP server on a given port._  |
|   | [**~Server**](#function-server) () <br>_Destructor for the_ [_**Server**_](classServer.md) _class._ |




























# Detailed Description


The [**Server**](classServer.md) class is responsible for managing all incoming and outgoing network communication, handling player actions, managing rooms, and maintaining game-related systems (movement, collision, shooting, etc.). 


    
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



### variable \_name 

```C++
std::string Server::_name;
```




<hr>



### variable coinTimer 

```C++
TimeManager Server::coinTimer;
```




<hr>



### variable coin\_count 

```C++
u_int16_t Server::coin_count;
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



### variable projectile\_count 

```C++
u_int16_t Server::projectile_count;
```




<hr>



### variable registry 

```C++
Registry Server::registry;
```




<hr>



### variable shoot 

```C++
ShootSystem Server::shoot;
```




<hr>



### variable shootTimer 

```C++
TimeManager Server::shootTimer;
```




<hr>



### variable updateTimer 

```C++
TimeManager Server::updateTimer;
```




<hr>
## Public Functions Documentation




### function Server 

_Constructs a new_ [_**Server**_](classServer.md) _object._
```C++
Server::Server (
    boost::asio::io_context & io_context,
    server_t server_me
) 
```





**Parameters:**


* `io_context` The Boost ASIO IO context to manage asynchronous operations. 
* `server_me` A struct containing TCP and UDP port numbers. 




        

<hr>



### function check\_player\_message 

_Verifies and processes a player's incoming message._ 
```C++
void Server::check_player_message (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the message was received. 
* `buffer` The message data from the client. 
* `client_endpoint` The endpoint (IP address and port) of the client. 




        

<hr>



### function check\_player\_position 

_Checks and updates the player's position._ 
```C++
void Server::check_player_position (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the message was received. 
* `buffer` The message data containing the player's position. 
* `client_endpoint` The endpoint of the client. 




        

<hr>



### function get\_player\_entity 

_Retrieves the entity representing the player based on their name._ 
```C++
Entity & Server::get_player_entity (
    const std::string & player_name
) 
```





**Parameters:**


* `player_name` The player's name. 



**Returns:**

The [**Entity**](classEntity.md) object representing the player. 





        

<hr>



### function get\_player\_id 

_Retrieves the player's ID based on their endpoint._ 
```C++
int Server::get_player_id (
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `client_endpoint` The endpoint of the client. 



**Returns:**

The player's ID. 





        

<hr>



### function get\_player\_name 

_Retrieves the player's name based on their endpoint._ 
```C++
std::string Server::get_player_name (
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `client_endpoint` The endpoint of the client. 



**Returns:**

The player's name. 





        

<hr>



### function handle\_client\_ping 

_Handles a ping message from a client to update the last communication time._ 
```C++
void Server::handle_client_ping (
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `client_endpoint` The endpoint (IP address and port) of the client who sent the ping. 




        

<hr>



### function handle\_list\_rooms 

_Handles a client's request to list all available rooms._ 
```C++
void Server::handle_list_rooms (
    udp::socket & socket,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the request was received. 
* `client_endpoint` The endpoint of the client requesting the list. 




        

<hr>



### function handle\_room\_creation 

_Handles the creation of a new room._ 
```C++
void Server::handle_room_creation (
    udp::socket & socket,
    const std::string & room_name,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the message was received. 
* `room_name` The name of the new room to create. 
* `client_endpoint` The endpoint (IP address and port) of the client creating the room. 




        

<hr>



### function handle\_room\_joining 

_Handles a client's request to join an existing room._ 
```C++
void Server::handle_room_joining (
    udp::socket & socket,
    int room_id,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the request was received. 
* `room_id` The ID of the room the client wants to join. 
* `client_endpoint` The endpoint (IP address and port) of the client. 




        

<hr>



### function handle\_tcp\_connection 

_Handles a new TCP connection from a client._ 
```C++
void Server::handle_tcp_connection (
    boost::asio::io_context & io_context,
    tcp::socket socket
) 
```





**Parameters:**


* `io_context` The IO context to manage asynchronous operations. 
* `socket` The TCP socket representing the connection with the client. 




        

<hr>



### function notify\_clients\_of\_disconnection 

_Notifies all connected clients about a client's disconnection._ 
```C++
void Server::notify_clients_of_disconnection (
    boost::asio::io_context & io_context,
    const udp::endpoint & disconnected_client
) 
```





**Parameters:**


* `io_context` The IO context to manage asynchronous operations. 
* `disconnected_client` The endpoint of the client who disconnected. 




        

<hr>



### function process\_message 

_Processes an incoming UDP message from a client._ 
```C++
void Server::process_message (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the message was received. 
* `buffer` The message data received from the client. 
* `client_endpoint` The endpoint (IP address and port) of the client who sent the message. 




        

<hr>



### function process\_message\_contain 

_Processes messages containing specific game data from a client._ 
```C++
void Server::process_message_contain (
    udp::socket & socket,
    const std::vector< uint8_t > & buffer,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which the message was received. 
* `buffer` The message data containing game-related content. 
* `client_endpoint` The endpoint (IP address and port) of the client. 




        

<hr>



### function run\_game 

```C++
void Server::run_game () 
```




<hr>



### function send\_udp\_with\_ack 

_Sends a UDP message to a client with acknowledgment support._ 
```C++
void Server::send_udp_with_ack (
    udp::socket & socket,
    const std::vector< uint8_t > & message,
    const udp::endpoint & client_endpoint
) 
```





**Parameters:**


* `socket` The UDP socket through which to send the message. 
* `message` The message data to send. 
* `client_endpoint` The endpoint (IP address and port) of the client. 




        

<hr>



### function start\_heartbeat\_monitor 

_Starts monitoring the heartbeat of connected clients._ 
```C++
void Server::start_heartbeat_monitor (
    boost::asio::io_context & io_context
) 
```





**Parameters:**


* `io_context` The IO context to manage asynchronous operations. 




        

<hr>



### function start\_tcp\_server 

_Starts the TCP server on a given port._ 
```C++
void Server::start_tcp_server (
    boost::asio::io_context & io_context,
    int port
) 
```





**Parameters:**


* `io_context` The IO context to manage asynchronous operations. 
* `port` The port number on which the TCP server listens. 




        

<hr>



### function start\_udp\_server 

_Starts the UDP server on a given port._ 
```C++
void Server::start_udp_server (
    boost::asio::io_context & io_context,
    int port
) 
```





**Parameters:**


* `io_context` The IO context to manage asynchronous operations. 
* `port` The port number on which the UDP server listens. 




        

<hr>



### function ~Server 

```C++
Server::~Server () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Server.hpp`

