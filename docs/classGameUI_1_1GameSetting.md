

# Class GameUI::GameSetting



[**ClassList**](annotated.md) **>** [**GameUI**](namespaceGameUI.md) **>** [**GameSetting**](classGameUI_1_1GameSetting.md)





* `#include <GameSetting.hpp>`



Inherits the following classes: [IScreen](classIScreen.md)






















































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**GameSetting**](#function-gamesetting) ([**ScreenManager**](classGameUI_1_1ScreenManager.md) & screenManager) <br> |
|  void | [**drawBackground**](#function-drawbackground) (sf::RenderWindow & window) <br> |
|  void | [**drawGameSetting**](#function-drawgamesetting) (sf::RenderWindow & window) <br> |
|  const sf::Sprite & | [**getBackgroundSprite**](#function-getbackgroundsprite) () const<br> |
|  [**AudioManager**](classAudioManager.md) & | [**getButtonSound**](#function-getbuttonsound) () <br> |
|  const sf::Sprite & | [**getGameSettingSprite**](#function-getgamesettingsprite) () const<br> |
|  sf::RectangleShape & | [**getRect1**](#function-getrect1) () <br> |
|  sf::RectangleShape & | [**getRect2**](#function-getrect2) () <br> |
| virtual void | [**handleEvent**](#function-handleevent) (sf::Event & event) override<br> |
|  void | [**loadFont**](#function-loadfont) (const std::string & fontPath) <br> |
| virtual void | [**render**](#function-render) (sf::RenderWindow & window) override<br> |
|  bool | [**setBackground**](#function-setbackground) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
|  bool | [**setGameSetting**](#function-setgamesetting) (const std::string & filePath, float windowWidth, float windowHeight) <br> |
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




### function GameSetting 

```C++
GameUI::GameSetting::GameSetting (
    ScreenManager & screenManager
) 
```




<hr>



### function drawBackground 

```C++
void GameUI::GameSetting::drawBackground (
    sf::RenderWindow & window
) 
```




<hr>



### function drawGameSetting 

```C++
void GameUI::GameSetting::drawGameSetting (
    sf::RenderWindow & window
) 
```




<hr>



### function getBackgroundSprite 

```C++
const sf::Sprite & GameUI::GameSetting::getBackgroundSprite () const
```




<hr>



### function getButtonSound 

```C++
inline AudioManager & GameUI::GameSetting::getButtonSound () 
```




<hr>



### function getGameSettingSprite 

```C++
const sf::Sprite & GameUI::GameSetting::getGameSettingSprite () const
```




<hr>



### function getRect1 

```C++
inline sf::RectangleShape & GameUI::GameSetting::getRect1 () 
```




<hr>



### function getRect2 

```C++
inline sf::RectangleShape & GameUI::GameSetting::getRect2 () 
```




<hr>



### function handleEvent 

```C++
virtual void GameUI::GameSetting::handleEvent (
    sf::Event & event
) override
```



Implements [*IScreen::handleEvent*](classIScreen.md#function-handleevent)


<hr>



### function loadFont 

```C++
void GameUI::GameSetting::loadFont (
    const std::string & fontPath
) 
```




<hr>



### function render 

```C++
virtual void GameUI::GameSetting::render (
    sf::RenderWindow & window
) override
```



Implements [*IScreen::render*](classIScreen.md#function-render)


<hr>



### function setBackground 

```C++
bool GameUI::GameSetting::setBackground (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function setGameSetting 

```C++
bool GameUI::GameSetting::setGameSetting (
    const std::string & filePath,
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function shapebuilder 

```C++
void GameUI::GameSetting::shapebuilder (
    sf::RenderWindow & window
) 
```




<hr>



### function update 

```C++
virtual void GameUI::GameSetting::update () override
```



Implements [*IScreen::update*](classIScreen.md#function-update)


<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/GameSetting.hpp`

