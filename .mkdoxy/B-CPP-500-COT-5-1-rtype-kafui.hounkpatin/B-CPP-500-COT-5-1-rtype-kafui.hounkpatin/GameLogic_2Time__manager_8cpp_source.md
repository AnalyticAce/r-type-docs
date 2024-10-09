

# File Time\_manager.cpp

[**File List**](files.md) **>** [**GameLogic**](dir_43a675281a639807a8e84134baca4472.md) **>** [**Time\_manager.cpp**](GameLogic_2Time__manager_8cpp.md)

[Go to the documentation of this file](GameLogic_2Time__manager_8cpp.md)


```C++
/*
** EPITECH PROJECT, 2024
** game_logic
** File description:
** Time_manager.cpp
*/

#include "Time_manager.hpp"

void TimeManager::restart() { start = std::chrono::steady_clock::now(); }

float TimeManager::getElapsedTimeInSeconds() const {
  auto now = std::chrono::steady_clock::now();
  std::chrono::duration<float> elapsed = now - start;
  return elapsed.count();
}
```


