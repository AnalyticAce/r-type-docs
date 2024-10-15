

# Class Client



[**ClassList**](annotated.md) **>** [**Client**](classClient.md)





* `#include <Client.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  [**AudioManager**](classAudioManager.md) | [**ButtonSound**](#variable-buttonsound)  <br> |
|  [**ImageManager**](classImageManager.md) | [**GamePlayImage**](#variable-gameplayimage)  <br> |
|  [**ImageManager**](classImageManager.md) | [**LifeBoardImage**](#variable-lifeboardimage)  <br> |
|  [**ImageManager**](classImageManager.md) | [**TeamScoreImage**](#variable-teamscoreimage)  <br> |
|  int | [**\_health**](#variable-_health)   = = 100<br> |
|  boost::asio::io\_context | [**\_io\_context**](#variable-_io_context)  <br> |
|  udp::endpoint | [**\_receiver\_endpoint**](#variable-_receiver_endpoint)  <br> |
|  int | [**\_score**](#variable-_score)   = = 0<br> |
|  udp::socket | [**\_soc**](#variable-_soc)  <br> |
|  [**ImageManager**](classImageManager.md) | [**backgroundImage**](#variable-backgroundimage)  <br> |
|  std::vector&lt; std::pair&lt; int, std::string &gt; &gt; | [**color\_by\_enemie**](#variable-color_by_enemie)  <br> |
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
|  std::vector&lt; sf::CircleShape &gt; | [**enemies**](#variable-enemies)  <br> |
|  std::vector&lt; std::pair&lt; int, [**Animation**](classAnimation.md) &gt; &gt; | [**enemies\_id**](#variable-enemies_id)  <br> |
|  sf::Event | [**event**](#variable-event)  <br> |
|  sf::Font | [**font**](#variable-font)  <br> |
|  bool | [**game\_over**](#variable-game_over)   = = false<br> |
|  std::string | [**input**](#variable-input)  <br> |
|  [**Animation**](classAnimation.md) | [**player1**](#variable-player1)  <br> |
|  [**Animation**](classAnimation.md) | [**player2**](#variable-player2)  <br> |
|  std::vector&lt; sf::RectangleShape &gt; | [**players**](#variable-players)  <br> |
|  std::vector&lt; std::pair&lt; int, [**Animation**](classAnimation.md) &gt; &gt; | [**players\_id**](#variable-players_id)  <br> |
|  std::vector&lt; sf::CircleShape &gt; | [**projectiles**](#variable-projectiles)  <br> |
|  std::vector&lt; std::pair&lt; int, sf::CircleShape &gt; &gt; | [**projectiles\_id**](#variable-projectiles_id)  <br> |
|  [**ShapeManager**](classShapeManager.md) | [**shapeManager1**](#variable-shapemanager1)  <br> |
|  [**ShapeManager**](classShapeManager.md) | [**shapeManager2**](#variable-shapemanager2)  <br> |
|  sf::RenderWindow | [**window**](#variable-window)  <br> |
|  [**TextManager**](classTextManager.md) | [**window\_manager**](#variable-window_manager)  <br> |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Client**](#function-client) () <br> |
|  void | [**assign\_enemy**](#function-assign_enemy) () <br> |
|  void | [**create\_player\_1**](#function-create_player_1) () <br> |
|  void | [**create\_player\_2**](#function-create_player_2) () <br> |
|  void | [**create\_player\_3**](#function-create_player_3) () <br> |
|  void | [**create\_player\_4**](#function-create_player_4) () <br> |
|  [**Animation**](classAnimation.md) | [**create\_random\_enemy**](#function-create_random_enemy) (int id) <br> |
|  std::string | [**get\_enemy\_color**](#function-get_enemy_color) (int id) <br> |
|  std::string | [**get\_name**](#function-get_name) () <br> |
|  std::string | [**get\_player\_color**](#function-get_player_color) (int id) <br> |
|  void | [**send\_tcp\_message**](#function-send_tcp_message) (const [**protocol::PlayerAction**](structprotocol_1_1PlayerAction.md) & message, const std::string & server\_ip, int server\_port) <br> |
|  void | [**send\_udp\_message**](#function-send_udp_message) (const [**protocol::PlayerAction**](structprotocol_1_1PlayerAction.md) & message, const std::string & server\_ip, int server\_port, std::string player\_name) <br> |
|   | [**~Client**](#function-client) () <br> |




























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



### variable color\_by\_enemie 

```C++
std::vector<std::pair<int, std::string> > Client::color_by_enemie;
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

```C++
Animation Client::create_random_enemy (
    int id
) 
```




<hr>



### function get\_enemy\_color 

```C++
std::string Client::get_enemy_color (
    int id
) 
```




<hr>



### function get\_name 

```C++
std::string Client::get_name () 
```




<hr>



### function get\_player\_color 

```C++
std::string Client::get_player_color (
    int id
) 
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
    int server_port,
    std::string player_name
) 
```




<hr>



### function ~Client 

```C++
Client::~Client () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Client.hpp`

