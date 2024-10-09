

# Class Room\_System



[**ClassList**](annotated.md) **>** [**Room\_System**](classRoom__System.md)





* `#include <room_system.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**Room\_System**](#function-room_system) () <br> |
|  int | [**create\_room**](#function-create_room) (const std::string & room\_name, int max\_players) <br> |
|  bool | [**join\_room**](#function-join_room) (int room\_id, const std::string & player\_name) <br> |
|  void | [**leave\_room**](#function-leave_room) (int room\_id, const std::string & player\_name) <br> |
|  std::vector&lt; std::string &gt; | [**list\_available\_rooms**](#function-list_available_rooms) () const<br> |
|  void | [**remove\_room**](#function-remove_room) (int room\_id) <br> |
|  void | [**start\_game\_in\_room**](#function-start_game_in_room) (int room\_id) <br> |
|   | [**~Room\_System**](#function-room_system) () <br> |




























## Public Functions Documentation




### function Room\_System 

```C++
Room_System::Room_System () 
```




<hr>



### function create\_room 

```C++
int Room_System::create_room (
    const std::string & room_name,
    int max_players
) 
```




<hr>



### function join\_room 

```C++
bool Room_System::join_room (
    int room_id,
    const std::string & player_name
) 
```




<hr>



### function leave\_room 

```C++
void Room_System::leave_room (
    int room_id,
    const std::string & player_name
) 
```




<hr>



### function list\_available\_rooms 

```C++
std::vector< std::string > Room_System::list_available_rooms () const
```




<hr>



### function remove\_room 

```C++
void Room_System::remove_room (
    int room_id
) 
```




<hr>



### function start\_game\_in\_room 

```C++
void Room_System::start_game_in_room (
    int room_id
) 
```




<hr>



### function ~Room\_System 

```C++
Room_System::~Room_System () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Server/include/room_system.hpp`

