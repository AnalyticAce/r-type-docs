

# Class Client



[**ClassList**](annotated.md) **>** [**Client**](classClient.md)



_Manages the client's interaction with the server and handles rendering, networking, and gameplay logic._ [More...](#detailed-description)

* `#include <Client.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  [**AudioManager**](classAudioManager.md) | [**ButtonSound**](#variable-buttonsound)  <br>_Manager for handling button sounds._  |
|  [**ImageManager**](classImageManager.md) | [**GamePlayImage**](#variable-gameplayimage)  <br>_Image managers for rendering various game assets._  |
|  [**ImageManager**](classImageManager.md) | [**LifeBoardImage**](#variable-lifeboardimage)  <br> |
|  [**ImageManager**](classImageManager.md) | [**TeamScoreImage**](#variable-teamscoreimage)  <br> |
|  int | [**\_health**](#variable-_health)   = = 100<br>_The current health of the player._  |
|  boost::asio::io\_context | [**\_io\_context**](#variable-_io_context)  <br>_The Boost Asio context for managing asynchronous operations._  |
|  udp::endpoint | [**\_receiver\_endpoint**](#variable-_receiver_endpoint)  <br>_The server's endpoint for UDP communication._  |
|  int | [**\_score**](#variable-_score)   = = 0<br>_The current score of the player._  |
|  udp::socket | [**\_soc**](#variable-_soc)  <br>_The UDP socket for communication with the server._  |
|  [**ImageManager**](classImageManager.md) | [**backgroundImage**](#variable-backgroundimage)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie1**](#variable-enemie1)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie2**](#variable-enemie2)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie3**](#variable-enemie3)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie4**](#variable-enemie4)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie5**](#variable-enemie5)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie6**](#variable-enemie6)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie7**](#variable-enemie7)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie8**](#variable-enemie8)  <br> |
|  [**Animation**](classAnimation.md) | [**enemie9**](#variable-enemie9)  <br> |
|  [**Animation**](classAnimation.md) | [**enemieBoss**](#variable-enemieboss)  <br> |
|  std::vector&lt; sf::CircleShape &gt; | [**enemies**](#variable-enemies)  <br>_List of enemy shapes._  |
|  std::vector&lt; std::pair&lt; int, [**Animation**](classAnimation.md) &gt; &gt; | [**enemies\_id**](#variable-enemies_id)  <br>_List of enemy IDs and their animations._  |
|  sf::Event | [**event**](#variable-event)  <br>_The event object used to handle player input and window events._  |
|  sf::Font | [**font**](#variable-font)  <br>_Font used for rendering text in the game._  |
|  bool | [**game\_over**](#variable-game_over)   = = false<br>_Whether the game has ended or not._  |
|  std::string | [**input**](#variable-input)  <br>[_**Input**_](classInput.md) _string for capturing user data._ |
|  [**Animation**](classAnimation.md) | [**player1**](#variable-player1)  <br>_Animations for players and enemies._  |
|  [**Animation**](classAnimation.md) | [**player2**](#variable-player2)  <br> |
|  std::vector&lt; sf::RectangleShape &gt; | [**players**](#variable-players)  <br>_List of player shapes in the game._  |
|  std::vector&lt; std::pair&lt; int, [**Animation**](classAnimation.md) &gt; &gt; | [**players\_id**](#variable-players_id)  <br>_List of player IDs and their corresponding animations._  |
|  std::vector&lt; sf::CircleShape &gt; | [**projectiles**](#variable-projectiles)  <br>_List of projectiles._  |
|  std::vector&lt; std::pair&lt; int, sf::CircleShape &gt; &gt; | [**projectiles\_id**](#variable-projectiles_id)  <br>_List of projectile IDs and shapes._  |
|  [**ShapeManager**](classShapeManager.md) | [**shapeManager1**](#variable-shapemanager1)  <br>_Shape managers for rendering various objects in the game._  |
|  [**ShapeManager**](classShapeManager.md) | [**shapeManager2**](#variable-shapemanager2)  <br> |
|  sf::RenderWindow | [**window**](#variable-window)  <br>_The main window used for rendering the game._  |
|  [**TextManager**](classTextManager.md) | [**window\_manager**](#variable-window_manager)  <br>_Manager for rendering text in the game window._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Client**](#function-client) () <br>_Default constructor for initializing the_ [_**Client**_](classClient.md) _._ |
|  void | [**assign\_enemy**](#function-assign_enemy) () <br>_Assigns enemy colors to specific IDs based on predefined values._  |
|  void | [**create\_player\_1**](#function-create_player_1) () <br>_Creates player 1 and adds it to the list of players._  |
|  void | [**create\_player\_2**](#function-create_player_2) () <br>_Creates player 2 and adds it to the list of players._  |
|  void | [**create\_player\_3**](#function-create_player_3) () <br>_Creates player 3 and adds it to the list of players._  |
|  void | [**create\_player\_4**](#function-create_player_4) () <br>_Creates player 4 and adds it to the list of players._  |
|  [**Animation**](classAnimation.md) | [**create\_random\_enemy**](#function-create_random_enemy) (int id) <br>_Creates an enemy entity with a random animation._  |
|  std::string | [**get\_enemy\_color**](#function-get_enemy_color) (int id) <br>_Retrieves the color associated with a specific enemy._  |
|  std::string | [**get\_name**](#function-get_name) () <br>_Retrieves the player's name from the input field._  |
|  std::string | [**get\_player\_color**](#function-get_player_color) (int id) <br>_Retrieves the color associated with a specific player._  |
|  void | [**send\_tcp\_message**](#function-send_tcp_message) (const [**protocol::PlayerAction**](structprotocol_1_1PlayerAction.md) & message, const std::string & server\_ip, int server\_port) <br>_Sends a TCP message containing a player's action to the server._  |
|  void | [**send\_udp\_message**](#function-send_udp_message) (const [**protocol::PlayerAction**](structprotocol_1_1PlayerAction.md) & message, const std::string & server\_ip, int server\_port, std::string player\_name) <br>_Sends a UDP message containing a player's action to the server._  |
|   | [**~Client**](#function-client) () <br>_Destructor to clean up resources._  |








## Protected Attributes

| Type | Name |
| ---: | :--- |
|  int | [**server\_tcp\_ip**](#variable-server_tcp_ip)  <br>_The TCP IP address of the server._  |
|  int | [**server\_udp\_ip**](#variable-server_udp_ip)  <br>_The UDP IP address of the server._  |




















# Detailed Description


This class establishes the client's connection to the game server using both UDP and TCP protocols. It also manages rendering the game window, handling user input, and managing entities such as players, enemies, and projectiles. The class integrates various managers (image, audio, shape, text) for smooth gameplay.




**Note:**

The client interacts with the server through `send_tcp_message` and `send_udp_message`. It also manages various players, enemies, and their animations. 





    
## Public Attributes Documentation




### variable ButtonSound 

```C++
AudioManager Client::ButtonSound;
```




<hr>



### variable GamePlayImage 

```C++
ImageManager Client::GamePlayImage;
```




<hr>



### variable LifeBoardImage 

```C++
ImageManager Client::LifeBoardImage;
```




<hr>



### variable TeamScoreImage 

```C++
ImageManager Client::TeamScoreImage;
```




<hr>



### variable \_health 

```C++
int Client::_health;
```




<hr>



### variable \_io\_context 

```C++
boost::asio::io_context Client::_io_context;
```




<hr>



### variable \_receiver\_endpoint 

```C++
udp::endpoint Client::_receiver_endpoint;
```




<hr>



### variable \_score 

```C++
int Client::_score;
```




<hr>



### variable \_soc 

```C++
udp::socket Client::_soc;
```




<hr>



### variable backgroundImage 

```C++
ImageManager Client::backgroundImage;
```




<hr>



### variable enemie1 

```C++
Animation Client::enemie1;
```




<hr>



### variable enemie2 

```C++
Animation Client::enemie2;
```




<hr>



### variable enemie3 

```C++
Animation Client::enemie3;
```




<hr>



### variable enemie4 

```C++
Animation Client::enemie4;
```




<hr>



### variable enemie5 

```C++
Animation Client::enemie5;
```




<hr>



### variable enemie6 

```C++
Animation Client::enemie6;
```




<hr>



### variable enemie7 

```C++
Animation Client::enemie7;
```




<hr>



### variable enemie8 

```C++
Animation Client::enemie8;
```




<hr>



### variable enemie9 

```C++
Animation Client::enemie9;
```




<hr>



### variable enemieBoss 

```C++
Animation Client::enemieBoss;
```




<hr>



### variable enemies 

```C++
std::vector<sf::CircleShape> Client::enemies;
```




<hr>



### variable enemies\_id 

```C++
std::vector<std::pair<int, Animation> > Client::enemies_id;
```




<hr>



### variable event 

```C++
sf::Event Client::event;
```




<hr>



### variable font 

```C++
sf::Font Client::font;
```




<hr>



### variable game\_over 

```C++
bool Client::game_over;
```




<hr>



### variable input 

```C++
std::string Client::input;
```




<hr>



### variable player1 

```C++
Animation Client::player1;
```




<hr>



### variable player2 

```C++
Animation Client::player2;
```




<hr>



### variable players 

```C++
std::vector<sf::RectangleShape> Client::players;
```




<hr>



### variable players\_id 

```C++
std::vector<std::pair<int, Animation> > Client::players_id;
```




<hr>



### variable projectiles 

```C++
std::vector<sf::CircleShape> Client::projectiles;
```




<hr>



### variable projectiles\_id 

```C++
std::vector<std::pair<int, sf::CircleShape> > Client::projectiles_id;
```




<hr>



### variable shapeManager1 

```C++
ShapeManager Client::shapeManager1;
```




<hr>



### variable shapeManager2 

```C++
ShapeManager Client::shapeManager2;
```




<hr>



### variable window 

```C++
sf::RenderWindow Client::window;
```




<hr>



### variable window\_manager 

```C++
TextManager Client::window_manager;
```




<hr>
## Public Functions Documentation




### function Client 

```C++
Client::Client () 
```




<hr>



### function assign\_enemy 

```C++
void Client::assign_enemy () 
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



### function create\_random\_enemy 

_Creates an enemy entity with a random animation._ 
```C++
Animation Client::create_random_enemy (
    int id
) 
```





**Parameters:**


* `id` The unique ID of the enemy to be created. 



**Returns:**

The animation object representing the enemy. 





        

<hr>



### function get\_enemy\_color 

_Retrieves the color associated with a specific enemy._ 
```C++
std::string Client::get_enemy_color (
    int id
) 
```





**Parameters:**


* `id` The ID of the enemy. 



**Returns:**

A string representing the enemy's color. 





        

<hr>



### function get\_name 

_Retrieves the player's name from the input field._ 
```C++
std::string Client::get_name () 
```





**Returns:**

A string representing the player's name. 





        

<hr>



### function get\_player\_color 

_Retrieves the color associated with a specific player._ 
```C++
std::string Client::get_player_color (
    int id
) 
```





**Parameters:**


* `id` The ID of the player. 



**Returns:**

A string representing the player's color. 





        

<hr>



### function send\_tcp\_message 

_Sends a TCP message containing a player's action to the server._ 
```C++
void Client::send_tcp_message (
    const protocol::PlayerAction & message,
    const std::string & server_ip,
    int server_port
) 
```





**Parameters:**


* `message` The player action to send. 
* `server_ip` The IP address of the server. 
* `server_port` The TCP port on which the server is listening. 




        

<hr>



### function send\_udp\_message 

_Sends a UDP message containing a player's action to the server._ 
```C++
void Client::send_udp_message (
    const protocol::PlayerAction & message,
    const std::string & server_ip,
    int server_port,
    std::string player_name
) 
```





**Parameters:**


* `message` The player action to send. 
* `server_ip` The IP address of the server. 
* `server_port` The UDP port on which the server is listening. 
* `player_name` The name of the player sending the message.



**Note:**

UDP is used for fast, lightweight communication. Messages may not always be delivered, so ACK mechanisms may be necessary. 





        

<hr>



### function ~Client 

```C++
Client::~Client () 
```




<hr>
## Protected Attributes Documentation




### variable server\_tcp\_ip 

```C++
int Client::server_tcp_ip;
```




<hr>



### variable server\_udp\_ip 

```C++
int Client::server_udp_ip;
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Client.hpp`

