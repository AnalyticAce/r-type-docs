

# Class Client



[**ClassList**](annotated.md) **>** [**Client**](classClient.md)





* `#include <Client.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::vector&lt; sf::CircleShape &gt; | [**enemies**](#variable-enemies)  <br> |
|  std::vector&lt; std::pair&lt; int, sf::CircleShape &gt; &gt; | [**enemies\_id**](#variable-enemies_id)  <br> |
|  sf::Event | [**event**](#variable-event)  <br> |
|  std::vector&lt; sf::RectangleShape &gt; | [**players**](#variable-players)  <br> |
|  std::vector&lt; std::pair&lt; int, sf::RectangleShape &gt; &gt; | [**players\_id**](#variable-players_id)  <br> |
|  sf::RenderWindow | [**window**](#variable-window)  <br> |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Client**](#function-client) () <br> |
|  void | [**create\_player\_1**](#function-create_player_1) () <br> |
|  void | [**create\_player\_2**](#function-create_player_2) () <br> |
|  void | [**create\_player\_3**](#function-create_player_3) () <br> |
|  void | [**create\_player\_4**](#function-create_player_4) () <br> |
|  std::string | [**get\_name**](#function-get_name) () <br> |
|  void | [**send\_tcp\_message**](#function-send_tcp_message) (const [**protocol::PlayerAction**](structprotocol_1_1PlayerAction.md) & message, const std::string & server\_ip, int server\_port) <br> |
|  void | [**send\_udp\_message**](#function-send_udp_message) (const [**protocol::PlayerAction**](structprotocol_1_1PlayerAction.md) & message, const std::string & server\_ip, int server\_port) <br> |
|   | [**~Client**](#function-client) () <br> |




























## Public Attributes Documentation




### variable enemies 

```C++
std::vector<sf::CircleShape> Client::enemies;
```




<hr>



### variable enemies\_id 

```C++
std::vector<std::pair<int, sf::CircleShape> > Client::enemies_id;
```




<hr>



### variable event 

```C++
sf::Event Client::event;
```




<hr>



### variable players 

```C++
std::vector<sf::RectangleShape> Client::players;
```




<hr>



### variable players\_id 

```C++
std::vector<std::pair<int, sf::RectangleShape> > Client::players_id;
```




<hr>



### variable window 

```C++
sf::RenderWindow Client::window;
```




<hr>
## Public Functions Documentation




### function Client 

```C++
Client::Client () 
```




<hr>



### function create\_player\_1 

```C++
void Client::create_player_1 () 
```




<hr>



### function create\_player\_2 

```C++
void Client::create_player_2 () 
```




<hr>



### function create\_player\_3 

```C++
void Client::create_player_3 () 
```




<hr>



### function create\_player\_4 

```C++
void Client::create_player_4 () 
```




<hr>



### function get\_name 

```C++
std::string Client::get_name () 
```




<hr>



### function send\_tcp\_message 

```C++
void Client::send_tcp_message (
    const protocol::PlayerAction & message,
    const std::string & server_ip,
    int server_port
) 
```




<hr>



### function send\_udp\_message 

```C++
void Client::send_udp_message (
    const protocol::PlayerAction & message,
    const std::string & server_ip,
    int server_port
) 
```




<hr>



### function ~Client 

```C++
Client::~Client () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/include/Client.hpp`

