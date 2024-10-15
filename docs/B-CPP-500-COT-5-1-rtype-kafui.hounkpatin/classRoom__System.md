

# Class Room\_System



[**ClassList**](annotated.md) **>** [**Room\_System**](classRoom__System.md)



_Class responsible for managing game rooms._ 

* `#include <room_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Room\_System**](#function-room_system) () <br>_Constructor for_ [_**Room\_System**_](classRoom__System.md) _._ |
|  int | [**create\_room**](#function-create_room) (const std::string & room\_name, int max\_players) <br>_Creates a new room._  |
|  bool | [**join\_room**](#function-join_room) (int room\_id, const std::string & player\_name) <br>_Allows a player to join an existing room._  |
|  void | [**leave\_room**](#function-leave_room) (int room\_id, const std::string & player\_name) <br>_Allows a player to leave a room._  |
|  std::vector&lt; std::string &gt; | [**list\_available\_rooms**](#function-list_available_rooms) () const<br>_Lists all available rooms._  |
|  void | [**remove\_room**](#function-remove_room) (int room\_id) <br>_Removes a room._  |
|  void | [**start\_game\_in\_room**](#function-start_game_in_room) (int room\_id) <br>_Starts a game in the specified room._  |
|   | [**~Room\_System**](#function-room_system) () <br>_Destructor for_ [_**Room\_System**_](classRoom__System.md) _._ |




























## Public Functions Documentation




### function Room\_System 

```C++
Room_System::Room_System () 
```




<hr>



### function create\_room 

_Creates a new room._ 
```C++
int Room_System::create_room (
    const std::string & room_name,
    int max_players
) 
```





**Parameters:**


* `room_name` The name of the room to create. 
* `max_players` The maximum number of players allowed in the room. 



**Returns:**

An integer representing the room ID of the newly created room. 





        

<hr>



### function join\_room 

_Allows a player to join an existing room._ 
```C++
bool Room_System::join_room (
    int room_id,
    const std::string & player_name
) 
```





**Parameters:**


* `room_id` The ID of the room to join. 
* `player_name` The name of the player joining the room. 



**Returns:**

true if the player successfully joined the room, false otherwise. 





        

<hr>



### function leave\_room 

_Allows a player to leave a room._ 
```C++
void Room_System::leave_room (
    int room_id,
    const std::string & player_name
) 
```





**Parameters:**


* `room_id` The ID of the room to leave. 
* `player_name` The name of the player leaving the room. 




        

<hr>



### function list\_available\_rooms 

_Lists all available rooms._ 
```C++
std::vector< std::string > Room_System::list_available_rooms () const
```





**Returns:**

A vector of strings containing the names of available rooms. 





        

<hr>



### function remove\_room 

_Removes a room._ 
```C++
void Room_System::remove_room (
    int room_id
) 
```





**Parameters:**


* `room_id` The ID of the room to remove. 




        

<hr>



### function start\_game\_in\_room 

_Starts a game in the specified room._ 
```C++
void Room_System::start_game_in_room (
    int room_id
) 
```





**Parameters:**


* `room_id` The ID of the room where the game should start. 




        

<hr>



### function ~Room\_System 

```C++
Room_System::~Room_System () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/room_system.hpp`

