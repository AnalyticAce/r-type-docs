

# Class GameUI::GameLobby



[**ClassList**](annotated.md) **>** [**GameUI**](namespaceGameUI.md) **>** [**GameLobby**](classGameUI_1_1GameLobby.md)





* `#include <GameLobby.hpp>`



Inherits the following classes: [IScreen](classIScreen.md)






















































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**GameLobby**](#function-gamelobby) ([**ScreenManager**](classGameUI_1_1ScreenManager.md) & screenManager) <br> |
|  void | [**drawAsteriodFour**](#function-drawasteriodfour) (sf::RenderWindow & window) <br> |
|  void | [**drawAsteriodOne**](#function-drawasteriodone) (sf::RenderWindow & window) <br> |
|  void | [**drawAsteriodThree**](#function-drawasteriodthree) (sf::RenderWindow & window) <br> |
|  void | [**drawAsteriodTwo**](#function-drawasteriodtwo) (sf::RenderWindow & window) <br> |
|  void | [**drawBackground**](#function-drawbackground) (sf::RenderWindow & window) <br> |
|  void | [**drawGameLobby**](#function-drawgamelobby) (sf::RenderWindow & window) <br> |
|  const sf::Sprite & | [**getAsteriodFourSprite**](#function-getasteriodfoursprite) () const<br> |
|  const sf::Sprite & | [**getAsteriodOneSprite**](#function-getasteriodonesprite) () const<br> |
|  const sf::Sprite & | [**getAsteriodThreeSprite**](#function-getasteriodthreesprite) () const<br> |
|  const sf::Sprite & | [**getAsteriodTwoSprite**](#function-getasteriodtwosprite) () const<br> |
|  const sf::Sprite & | [**getBackgroundSprite**](#function-getbackgroundsprite) () const<br> |
|  [**AudioManager**](classAudioManager.md) & | [**getButtonSound**](#function-getbuttonsound) () <br> |
|  const sf::Sprite & | [**getGameLobbySprite**](#function-getgamelobbysprite) () const<br> |
|  [**MouseManager**](classMouseManager.md) & | [**getMouse**](#function-getmouse) () <br> |
|  sf::RectangleShape & | [**getRect1**](#function-getrect1) () <br> |
|  sf::RectangleShape & | [**getRect2**](#function-getrect2) () <br> |
|  [**AudioManager**](classAudioManager.md) & | [**getRoomMusic**](#function-getroommusic) () <br> |
| virtual void | [**handleEvent**](#function-handleevent) (sf::Event & event) override<br> |
|  void | [**loadFont**](#function-loadfont) (const std::string & fontPath) <br> |
| virtual void | [**render**](#function-render) (sf::RenderWindow & window) override<br> |
|  bool | [**setAsteriodFour**](#function-setasteriodfour) (const std::string & filePath) <br> |
|  bool | [**setAsteriodOne**](#function-setasteriodone) (const std::string & filePath) <br> |
|  bool | [**setAsteriodThree**](#function-setasteriodthree) (const std::string & filePath) <br> |
|  bool | [**setAsteriodTwo**](#function-setasteriodtwo) (const std::string & filePath) <br> |
|  bool | [**setBackground**](#function-setbackground) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  bool | [**setGameLobby**](#function-setgamelobby) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  void | [**shapebuilder**](#function-shapebuilder) (sf::RenderWindow & window) <br> |
| virtual void | [**update**](#function-update) () override<br> |


## Public Functions inherited from IScreen

See [IScreen](classIScreen.md)

| Type | Name |
| ---: | :--- |
| virtual void | [**handleEvent**](classIScreen.md#function-handleevent) (sf::Event & event) = 0<br> |
| virtual void | [**render**](classIScreen.md#function-render) (sf::RenderWindow & window) = 0<br> |
| virtual void | [**update**](classIScreen.md#function-update) () = 0<br> |
| virtual  | [**~IScreen**](classIScreen.md#function-iscreen) () = default<br> |






















































## Public Functions Documentation




### function GameLobby 

```C++
GameUI::GameLobby::GameLobby (
    ScreenManager & screenManager
) 
```




<hr>



### function drawAsteriodFour 

```C++
void GameUI::GameLobby::drawAsteriodFour (
    sf::RenderWindow & window
) 
```




<hr>



### function drawAsteriodOne 

```C++
void GameUI::GameLobby::drawAsteriodOne (
    sf::RenderWindow & window
) 
```




<hr>



### function drawAsteriodThree 

```C++
void GameUI::GameLobby::drawAsteriodThree (
    sf::RenderWindow & window
) 
```




<hr>



### function drawAsteriodTwo 

```C++
void GameUI::GameLobby::drawAsteriodTwo (
    sf::RenderWindow & window
) 
```




<hr>



### function drawBackground 

```C++
void GameUI::GameLobby::drawBackground (
    sf::RenderWindow & window
) 
```




<hr>



### function drawGameLobby 

```C++
void GameUI::GameLobby::drawGameLobby (
    sf::RenderWindow & window
) 
```




<hr>



### function getAsteriodFourSprite 

```C++
const sf::Sprite & GameUI::GameLobby::getAsteriodFourSprite () const
```




<hr>



### function getAsteriodOneSprite 

```C++
const sf::Sprite & GameUI::GameLobby::getAsteriodOneSprite () const
```




<hr>



### function getAsteriodThreeSprite 

```C++
const sf::Sprite & GameUI::GameLobby::getAsteriodThreeSprite () const
```




<hr>



### function getAsteriodTwoSprite 

```C++
const sf::Sprite & GameUI::GameLobby::getAsteriodTwoSprite () const
```




<hr>



### function getBackgroundSprite 

```C++
const sf::Sprite & GameUI::GameLobby::getBackgroundSprite () const
```




<hr>



### function getButtonSound 

```C++
inline AudioManager & GameUI::GameLobby::getButtonSound () 
```




<hr>



### function getGameLobbySprite 

```C++
const sf::Sprite & GameUI::GameLobby::getGameLobbySprite () const
```




<hr>



### function getMouse 

```C++
inline MouseManager & GameUI::GameLobby::getMouse () 
```




<hr>



### function getRect1 

```C++
inline sf::RectangleShape & GameUI::GameLobby::getRect1 () 
```




<hr>



### function getRect2 

```C++
inline sf::RectangleShape & GameUI::GameLobby::getRect2 () 
```




<hr>



### function getRoomMusic 

```C++
inline AudioManager & GameUI::GameLobby::getRoomMusic () 
```




<hr>



### function handleEvent 

```C++
virtual void GameUI::GameLobby::handleEvent (
    sf::Event & event
) override
```



Implements [*IScreen::handleEvent*](classIScreen.md#function-handleevent)


<hr>



### function loadFont 

```C++
void GameUI::GameLobby::loadFont (
    const std::string & fontPath
) 
```




<hr>



### function render 

```C++
virtual void GameUI::GameLobby::render (
    sf::RenderWindow & window
) override
```



Implements [*IScreen::render*](classIScreen.md#function-render)


<hr>



### function setAsteriodFour 

```C++
bool GameUI::GameLobby::setAsteriodFour (
    const std::string & filePath
) 
```




<hr>



### function setAsteriodOne 

```C++
bool GameUI::GameLobby::setAsteriodOne (
    const std::string & filePath
) 
```




<hr>



### function setAsteriodThree 

```C++
bool GameUI::GameLobby::setAsteriodThree (
    const std::string & filePath
) 
```




<hr>



### function setAsteriodTwo 

```C++
bool GameUI::GameLobby::setAsteriodTwo (
    const std::string & filePath
) 
```




<hr>



### function setBackground 

```C++
bool GameUI::GameLobby::setBackground (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function setGameLobby 

```C++
bool GameUI::GameLobby::setGameLobby (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function shapebuilder 

```C++
void GameUI::GameLobby::shapebuilder (
    sf::RenderWindow & window
) 
```




<hr>



### function update 

```C++
virtual void GameUI::GameLobby::update () override
```



Implements [*IScreen::update*](classIScreen.md#function-update)


<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/GameLobby.hpp`

