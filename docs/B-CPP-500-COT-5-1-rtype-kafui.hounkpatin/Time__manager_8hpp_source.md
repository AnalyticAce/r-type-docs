

# File Time\_manager.hpp

[**File List**](files.md) **>** [**include**](dir_d44c64559bbebec7f509842c48db8b23.md) **>** [**Server**](dir_17f455aea618a06e8886390757d4c564.md) **>** [**Time\_manager.hpp**](Time__manager_8hpp.md)

[Go to the documentation of this file](Time__manager_8hpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Time_manager.hpp
*/

#ifndef TIME_MANAGER_HPP_
#define TIME_MANAGER_HPP_
#include <chrono>

#include "Entity.hpp"

class TimeManager
{
private:
    std::chrono::steady_clock::time_point start; 

public:
    TimeManager() : start(std::chrono::steady_clock::now()) {}

    void restart();

    float getElapsedTimeInSeconds() const;
};

#endif // TIME_MANAGER_HPP_
```


