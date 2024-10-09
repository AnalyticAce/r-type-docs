

# File InputManager.hpp

[**File List**](files.md) **>** [**Engine**](dir_7dd3fffce23fd825de4eb623b113c1bd.md) **>** [**Input**](dir_011a5bb273ab46acf9be02ac4bf7f0a3.md) **>** [**InputManager.hpp**](InputManager_8hpp.md)

[Go to the documentation of this file](InputManager_8hpp.md)


```C++
#ifndef INPUTMANAGER_HPP
#define INPUTMANAGER_HPP

#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>

class InputManager {
  struct Button {
    bool left;    
    bool right;   
    bool up;      
    bool down;    
    bool attack;  
    bool escape;  
  };

private:
  Button button;

public:
  InputManager();

  ~InputManager();

  void handleInput(sf::Event event, sf::RenderWindow &window);

  Button getButton(void) const;
};

#endif // INPUTMANAGER_HPP
```


