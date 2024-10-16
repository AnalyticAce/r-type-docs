

# Class IScreen



[**ClassList**](annotated.md) **>** [**IScreen**](classIScreen.md)





* `#include <ScreenManager.hpp>`





Inherited by the following classes: [GameUI::GameLobby](classGameUI_1_1GameLobby.md),  [GameUI::GamePlay](classGameUI_1_1GamePlay.md),  [GameUI::GameSetting](classGameUI_1_1GameSetting.md),  [GameUI::RoomLobby](classGameUI_1_1RoomLobby.md)
































## Public Functions

| Type | Name |
| ---: | :--- |
| virtual void | [**handleEvent**](#function-handleevent) (sf::Event & event) = 0<br> |
| virtual void | [**render**](#function-render) (sf::RenderWindow & window) = 0<br> |
| virtual void | [**update**](#function-update) () = 0<br> |
| virtual  | [**~IScreen**](#function-iscreen) () = default<br> |




























## Public Functions Documentation




### function handleEvent 

```C++
virtual void IScreen::handleEvent (
    sf::Event & event
) = 0
```




<hr>



### function render 

```C++
virtual void IScreen::render (
    sf::RenderWindow & window
) = 0
```




<hr>



### function update 

```C++
virtual void IScreen::update () = 0
```




<hr>



### function ~IScreen 

```C++
virtual IScreen::~IScreen () = default
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/ScreenManager.hpp`

