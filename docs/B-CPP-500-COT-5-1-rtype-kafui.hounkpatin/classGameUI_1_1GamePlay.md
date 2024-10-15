

# Class GameUI::GamePlay



[**ClassList**](annotated.md) **>** [**GameUI**](namespaceGameUI.md) **>** [**GamePlay**](classGameUI_1_1GamePlay.md)





* `#include <GamePlay.hpp>`



Inherits the following classes: [IScreen](classIScreen.md)






















## Public Attributes

| Type | Name |
| ---: | :--- |
|  bool | [**playIsDown**](#variable-playisdown)  <br> |
|  bool | [**playIsLeft**](#variable-playisleft)  <br> |
|  bool | [**playIsRight**](#variable-playisright)  <br> |
|  bool | [**playIsUp**](#variable-playisup)  <br> |
































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**GamePlay**](#function-gameplay) ([**ScreenManager**](classGameUI_1_1ScreenManager.md) & screenManager) <br> |
|  void | [**createEnamies5**](#function-createenamies5) () <br> |
|  void | [**createEnamies6**](#function-createenamies6) () <br> |
|  void | [**createEnamies7**](#function-createenamies7) () <br> |
|  void | [**createEnamies8**](#function-createenamies8) () <br> |
|  void | [**createEnamies9**](#function-createenamies9) () <br> |
|  void | [**createEnamiesBoss**](#function-createenamiesboss) () <br> |
|  void | [**createEnemies**](#function-createenemies) () <br> |
|  void | [**createEnemies2**](#function-createenemies2) () <br> |
|  void | [**createEnemies3**](#function-createenemies3) () <br> |
|  void | [**createEnemies4**](#function-createenemies4) () <br> |
|  void | [**createPlayer1**](#function-createplayer1) () <br> |
|  void | [**createPlayer2**](#function-createplayer2) () <br> |
|  void | [**drawBackground**](#function-drawbackground) (sf::RenderWindow & window) <br> |
|  void | [**drawLifeBoard**](#function-drawlifeboard) (sf::RenderWindow & window) <br> |
|  void | [**drawTeamScore**](#function-drawteamscore) (sf::RenderWindow & window) <br> |
|  const sf::Sprite & | [**getBackgroundSprite**](#function-getbackgroundsprite) () const<br> |
|  [**AudioManager**](classAudioManager.md) & | [**getButtonSound**](#function-getbuttonsound) () <br> |
|  const sf::Sprite & | [**getLifeBoardSprite**](#function-getlifeboardsprite) () const<br> |
|  const sf::Sprite & | [**getTeamScoreSprite**](#function-getteamscoresprite) () const<br> |
| virtual void | [**handleEvent**](#function-handleevent) (sf::Event & event) override<br> |
|  void | [**loadFont**](#function-loadfont) (const std::string & fontPath) <br> |
| virtual void | [**render**](#function-render) (sf::RenderWindow & window) override<br> |
|  bool | [**setBackground**](#function-setbackground) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  bool | [**setLifeBoard**](#function-setlifeboard) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  bool | [**setTeamScore**](#function-setteamscore) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  void | [**shapebuilder**](#function-shapebuilder) (sf::RenderWindow & window) <br> |
|  void | [**spawnRandomEnemies**](#function-spawnrandomenemies) () <br> |
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




### variable playIsDown 

```C++
bool GameUI::GamePlay::playIsDown;
```




<hr>



### variable playIsLeft 

```C++
bool GameUI::GamePlay::playIsLeft;
```




<hr>



### variable playIsRight 

```C++
bool GameUI::GamePlay::playIsRight;
```




<hr>



### variable playIsUp 

```C++
bool GameUI::GamePlay::playIsUp;
```




<hr>
## Public Functions Documentation




### function GamePlay 

```C++
GameUI::GamePlay::GamePlay (
    ScreenManager & screenManager
) 
```




<hr>



### function createEnamies5 

```C++
void GameUI::GamePlay::createEnamies5 () 
```




<hr>



### function createEnamies6 

```C++
void GameUI::GamePlay::createEnamies6 () 
```




<hr>



### function createEnamies7 

```C++
void GameUI::GamePlay::createEnamies7 () 
```




<hr>



### function createEnamies8 

```C++
void GameUI::GamePlay::createEnamies8 () 
```




<hr>



### function createEnamies9 

```C++
void GameUI::GamePlay::createEnamies9 () 
```




<hr>



### function createEnamiesBoss 

```C++
void GameUI::GamePlay::createEnamiesBoss () 
```




<hr>



### function createEnemies 

```C++
void GameUI::GamePlay::createEnemies () 
```




<hr>



### function createEnemies2 

```C++
void GameUI::GamePlay::createEnemies2 () 
```




<hr>



### function createEnemies3 

```C++
void GameUI::GamePlay::createEnemies3 () 
```




<hr>



### function createEnemies4 

```C++
void GameUI::GamePlay::createEnemies4 () 
```




<hr>



### function createPlayer1 

```C++
void GameUI::GamePlay::createPlayer1 () 
```




<hr>



### function createPlayer2 

```C++
void GameUI::GamePlay::createPlayer2 () 
```




<hr>



### function drawBackground 

```C++
void GameUI::GamePlay::drawBackground (
    sf::RenderWindow & window
) 
```




<hr>



### function drawLifeBoard 

```C++
void GameUI::GamePlay::drawLifeBoard (
    sf::RenderWindow & window
) 
```




<hr>



### function drawTeamScore 

```C++
void GameUI::GamePlay::drawTeamScore (
    sf::RenderWindow & window
) 
```




<hr>



### function getBackgroundSprite 

```C++
const sf::Sprite & GameUI::GamePlay::getBackgroundSprite () const
```




<hr>



### function getButtonSound 

```C++
inline AudioManager & GameUI::GamePlay::getButtonSound () 
```




<hr>



### function getLifeBoardSprite 

```C++
const sf::Sprite & GameUI::GamePlay::getLifeBoardSprite () const
```




<hr>



### function getTeamScoreSprite 

```C++
const sf::Sprite & GameUI::GamePlay::getTeamScoreSprite () const
```




<hr>



### function handleEvent 

```C++
virtual void GameUI::GamePlay::handleEvent (
    sf::Event & event
) override
```



Implements [*IScreen::handleEvent*](classIScreen.md#function-handleevent)


<hr>



### function loadFont 

```C++
void GameUI::GamePlay::loadFont (
    const std::string & fontPath
) 
```




<hr>



### function render 

```C++
virtual void GameUI::GamePlay::render (
    sf::RenderWindow & window
) override
```



Implements [*IScreen::render*](classIScreen.md#function-render)


<hr>



### function setBackground 

```C++
bool GameUI::GamePlay::setBackground (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function setLifeBoard 

```C++
bool GameUI::GamePlay::setLifeBoard (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function setTeamScore 

```C++
bool GameUI::GamePlay::setTeamScore (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function shapebuilder 

```C++
void GameUI::GamePlay::shapebuilder (
    sf::RenderWindow & window
) 
```




<hr>



### function spawnRandomEnemies 

```C++
void GameUI::GamePlay::spawnRandomEnemies () 
```




<hr>



### function update 

```C++
virtual void GameUI::GamePlay::update () override
```



Implements [*IScreen::update*](classIScreen.md#function-update)


<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/GamePlay.hpp`

