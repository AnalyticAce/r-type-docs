

# File Time\_manager.hpp

[**File List**](files.md) **>** [**include**](dir_fb85385106f6152c3d8f4b6fd945aed6.md) **>** [**Time\_manager.hpp**](Server_2include_2Time__manager_8hpp.md)

[Go to the documentation of this file](Server_2include_2Time__manager_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Time_manager.hpp
*/

#ifndef TIME_MANAGER_HPP_
#define TIME_MANAGER_HPP_
#include "Entity.hpp"
#include <chrono>
class TimeManager {
private:
  std::chrono::steady_clock::time_point start;

public:
  TimeManager() : start(std::chrono::steady_clock::now()) {}
  void restart();
  float getElapsedTimeInSeconds() const;
};

#endif // TIME_MANAGER_HPP_
```


