

# Class GameUI::RoomLobby



[**ClassList**](annotated.md) **>** [**GameUI**](namespaceGameUI.md) **>** [**RoomLobby**](classGameUI_1_1RoomLobby.md)





* `#include <RoomLobby.hpp>`



Inherits the following classes: [IScreen](classIScreen.md)






















## Public Attributes

| Type | Name |
| ---: | :--- |
|  std::string | [**inputIp**](#variable-inputip)  <br> |
|  std::string | [**inputName**](#variable-inputname)  <br> |
|  std::string | [**inputPort**](#variable-inputport)  <br> |
|  sf::Text | [**textip**](#variable-textip)  <br> |
|  sf::Text | [**textname**](#variable-textname)  <br> |
|  sf::Text | [**textport**](#variable-textport)  <br> |
































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**RoomLobby**](#function-roomlobby) ([**ScreenManager**](classGameUI_1_1ScreenManager.md) & screenManager) <br> |
|  void | [**drawBackButton**](#function-drawbackbutton) (sf::RenderWindow & window) <br> |
|  void | [**drawBackground**](#function-drawbackground) (sf::RenderWindow & window) <br> |
|  void | [**drawRoomLobby**](#function-drawroomlobby) (sf::RenderWindow & window) <br> |
|  const sf::Sprite & | [**getBackButtonSprite**](#function-getbackbuttonsprite) () const<br> |
|  const sf::Sprite & | [**getBackgroundSprite**](#function-getbackgroundsprite) () const<br> |
|  [**AudioManager**](classAudioManager.md) & | [**getButtonSound**](#function-getbuttonsound) () <br> |
|  [**MouseManager**](classMouseManager.md) & | [**getMouse**](#function-getmouse) () <br> |
|  sf::RectangleShape & | [**getRect1**](#function-getrect1) () <br> |
|  sf::RectangleShape & | [**getRect2**](#function-getrect2) () <br> |
|  sf::RectangleShape & | [**getRect3**](#function-getrect3) () <br> |
|  sf::RectangleShape & | [**getRect4**](#function-getrect4) () <br> |
|  const sf::Sprite & | [**getRoomLobbySprite**](#function-getroomlobbysprite) () const<br> |
|  sf::Text & | [**getTextIp**](#function-gettextip) () <br> |
|  sf::Text & | [**getTextName**](#function-gettextname) () <br> |
|  sf::Text & | [**getTextPort**](#function-gettextport) () <br> |
| virtual void | [**handleEvent**](#function-handleevent) (sf::Event & event) override<br> |
|  void | [**loadFont**](#function-loadfont) (const std::string & fontPath) <br> |
| virtual void | [**render**](#function-render) (sf::RenderWindow & window) override<br> |
|  bool | [**setBackButton**](#function-setbackbutton) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  bool | [**setBackground**](#function-setbackground) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  bool | [**setRoomLobby**](#function-setroomlobby) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  void | [**shapebuilder**](#function-shapebuilder) (sf::RenderWindow & window) <br> |
|  void | [**textfieldsetter**](#function-textfieldsetter) (sf::Font & font) <br> |
| virtual void | [**update**](#function-update) () override<br> |


## Public Functions inherited from IScreen

See [IScreen](classIScreen.md)

| Type | Name |
| ---: | :--- |
| virtual void | [**handleEvent**](classIScreen.md#function-handleevent) (sf::Event & event) = 0<br> |
| virtual void | [**render**](classIScreen.md#function-render) (sf::RenderWindow & window) = 0<br> |
| virtual void | [**update**](classIScreen.md#function-update) () = 0<br> |
| virtual  | [**~IScreen**](classIScreen.md#function-iscreen) () = default<br> |






















































## Public Attributes Documentation




### variable inputIp 

```C++
std::string GameUI::RoomLobby::inputIp;
```




<hr>



### variable inputName 

```C++
std::string GameUI::RoomLobby::inputName;
```




<hr>



### variable inputPort 

```C++
std::string GameUI::RoomLobby::inputPort;
```




<hr>



### variable textip 

```C++
sf::Text GameUI::RoomLobby::textip;
```




<hr>



### variable textname 

```C++
sf::Text GameUI::RoomLobby::textname;
```




<hr>



### variable textport 

```C++
sf::Text GameUI::RoomLobby::textport;
```




<hr>
## Public Functions Documentation




### function RoomLobby 

```C++
GameUI::RoomLobby::RoomLobby (
    ScreenManager & screenManager
) 
```




<hr>



### function drawBackButton 

```C++
void GameUI::RoomLobby::drawBackButton (
    sf::RenderWindow & window
) 
```




<hr>



### function drawBackground 

```C++
void GameUI::RoomLobby::drawBackground (
    sf::RenderWindow & window
) 
```




<hr>



### function drawRoomLobby 

```C++
void GameUI::RoomLobby::drawRoomLobby (
    sf::RenderWindow & window
) 
```




<hr>



### function getBackButtonSprite 

```C++
const sf::Sprite & GameUI::RoomLobby::getBackButtonSprite () const
```




<hr>



### function getBackgroundSprite 

```C++
const sf::Sprite & GameUI::RoomLobby::getBackgroundSprite () const
```




<hr>



### function getButtonSound 

```C++
inline AudioManager & GameUI::RoomLobby::getButtonSound () 
```




<hr>



### function getMouse 

```C++
inline MouseManager & GameUI::RoomLobby::getMouse () 
```




<hr>



### function getRect1 

```C++
inline sf::RectangleShape & GameUI::RoomLobby::getRect1 () 
```




<hr>



### function getRect2 

```C++
inline sf::RectangleShape & GameUI::RoomLobby::getRect2 () 
```




<hr>



### function getRect3 

```C++
inline sf::RectangleShape & GameUI::RoomLobby::getRect3 () 
```




<hr>



### function getRect4 

```C++
inline sf::RectangleShape & GameUI::RoomLobby::getRect4 () 
```




<hr>



### function getRoomLobbySprite 

```C++
const sf::Sprite & GameUI::RoomLobby::getRoomLobbySprite () const
```




<hr>



### function getTextIp 

```C++
inline sf::Text & GameUI::RoomLobby::getTextIp () 
```




<hr>



### function getTextName 

```C++
inline sf::Text & GameUI::RoomLobby::getTextName () 
```




<hr>



### function getTextPort 

```C++
inline sf::Text & GameUI::RoomLobby::getTextPort () 
```




<hr>



### function handleEvent 

```C++
virtual void GameUI::RoomLobby::handleEvent (
    sf::Event & event
) override
```



Implements [*IScreen::handleEvent*](classIScreen.md#function-handleevent)


<hr>



### function loadFont 

```C++
void GameUI::RoomLobby::loadFont (
    const std::string & fontPath
) 
```




<hr>



### function render 

```C++
virtual void GameUI::RoomLobby::render (
    sf::RenderWindow & window
) override
```



Implements [*IScreen::render*](classIScreen.md#function-render)


<hr>



### function setBackButton 

```C++
bool GameUI::RoomLobby::setBackButton (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function setBackground 

```C++
bool GameUI::RoomLobby::setBackground (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function setRoomLobby 

```C++
bool GameUI::RoomLobby::setRoomLobby (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function shapebuilder 

```C++
void GameUI::RoomLobby::shapebuilder (
    sf::RenderWindow & window
) 
```




<hr>



### function textfieldsetter 

```C++
void GameUI::RoomLobby::textfieldsetter (
    sf::Font & font
) 
```




<hr>



### function update 

```C++
virtual void GameUI::RoomLobby::update () override
```



Implements [*IScreen::update*](classIScreen.md#function-update)


<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/RoomLobby.hpp`

