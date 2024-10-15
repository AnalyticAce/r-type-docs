

# Class TimeManager



[**ClassList**](annotated.md) **>** [**TimeManager**](classTimeManager.md)



_A class to manage time tracking for elapsed time measurements._ 

* `#include <Time_manager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**TimeManager**](#function-timemanager) () <br>_Constructs a_ [_**TimeManager**_](classTimeManager.md) _and initializes the start time._ |
|  float | [**getElapsedTimeInSeconds**](#function-getelapsedtimeinseconds) () const<br>_Gets the elapsed time since the start time in seconds._  |
|  void | [**restart**](#function-restart) () <br>_Restarts the timer by resetting the start time to the current time._  |




























## Public Functions Documentation




### function TimeManager 

```C++
inline TimeManager::TimeManager () 
```




<hr>



### function getElapsedTimeInSeconds 

_Gets the elapsed time since the start time in seconds._ 
```C++
float TimeManager::getElapsedTimeInSeconds () const
```





**Returns:**

The elapsed time in seconds as a float. 





        

<hr>



### function restart 

```C++
void TimeManager::restart () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `include/Server/Time_manager.hpp`

