

# File Time\_manager.cpp

[**File List**](files.md) **>** [**Server**](dir_f6675a7e1cd1d6d7f6e5e9669ead62e8.md) **>** [**src**](dir_35da1b20ef5d00fba1377c2ea4ffeb70.md) **>** [**Time\_manager.cpp**](Server_2src_2Time__manager_8cpp.md)

[Go to the documentation of this file](Server_2src_2Time__manager_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Time_manager.cpp
*/

#include "../include/Time_manager.hpp"

void TimeManager::restart() { start = std::chrono::steady_clock::now(); }

float TimeManager::getElapsedTimeInSeconds() const {
  auto now = std::chrono::steady_clock::now();
  std::chrono::duration<float> elapsed = now - start;
  return elapsed.count();
}
```


