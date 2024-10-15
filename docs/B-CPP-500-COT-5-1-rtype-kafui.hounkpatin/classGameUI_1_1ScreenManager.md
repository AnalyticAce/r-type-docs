

# Class GameUI::ScreenManager



[**ClassList**](annotated.md) **>** [**GameUI**](namespaceGameUI.md) **>** [**ScreenManager**](classGameUI_1_1ScreenManager.md)





* `#include <ScreenManager.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  [**Client**](classClient.md) | [**client**](#variable-client)  <br> |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**ScreenManager**](#function-screenmanager) (sf::RenderWindow & window) <br> |
|  void | [**addScreen**](#function-addscreen) (const std::string & name, std::function&lt; std::unique\_ptr&lt; T &gt;()&gt; factory) <br> |
|  void | [**handleEvent**](#function-handleevent) (sf::Event & event) <br> |
|  void | [**render**](#function-render) () <br> |
|  void | [**switchToScreen**](#function-switchtoscreen) (const std::string & name) <br> |
|  void | [**update**](#function-update) () <br> |




























## Public Attributes Documentation




### variable client 

```C++
Client GameUI::ScreenManager::client;
```




<hr>
## Public Functions Documentation




### function ScreenManager 

```C++
GameUI::ScreenManager::ScreenManager (
    sf::RenderWindow & window
) 
```




<hr>



### function addScreen 

```C++
template<typename T>
inline void GameUI::ScreenManager::addScreen (
    const std::string & name,
    std::function< std::unique_ptr< T >()> factory
) 
```




<hr>



### function handleEvent 

```C++
void GameUI::ScreenManager::handleEvent (
    sf::Event & event
) 
```




<hr>



### function render 

```C++
void GameUI::ScreenManager::render () 
```




<hr>



### function switchToScreen 

```C++
void GameUI::ScreenManager::switchToScreen (
    const std::string & name
) 
```




<hr>



### function update 

```C++
void GameUI::ScreenManager::update () 
```




<hr>

------------------------------
The documentation for this class was generated from the following file `src/Client/ScreenManager.hpp`

