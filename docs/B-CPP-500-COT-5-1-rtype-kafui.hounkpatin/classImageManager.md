

# Class ImageManager



[**ClassList**](annotated.md) **>** [**ImageManager**](classImageManager.md)



_Handles image loading, manipulation, and rendering using the SFML graphics library._ [More...](#detailed-description)

* `#include <ImageManager.hpp>`





















## Public Attributes

| Type | Name |
| ---: | :--- |
|  sf::Texture | [**texture**](#variable-texture)  <br>_Texture object for storing the image data._  |
















## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**ImageManager**](#function-imagemanager) () <br>_Constructs an_ [_**ImageManager**_](classImageManager.md) _instance._ |
|  bool | [**createImage**](#function-createimage) (const std::string & filePath) <br>_Loads an image from the specified file path._  |
|  void | [**destroyImage**](#function-destroyimage) () <br>_Destroys the image and releases its resources._  |
|  void | [**draw**](#function-draw) (sf::RenderWindow & window) <br>_Draws the image sprite to the specified render window._  |
|  void | [**fitToScreen**](#function-fittoscreen) (float windowWidth, float windowHeight) <br> |
|  sf::FloatRect | [**getGlobalBounds**](#function-getglobalbounds) () <br>_Gets the global bounding rectangle of the sprite._  |
|  sf::Sprite & | [**getSprite**](#function-getsprite-12) () <br>_Sprite object for rendering the image._  |
|  const sf::Sprite & | [**getSprite**](#function-getsprite-22) () const<br> |
|  void | [**setPosition**](#function-setposition) (float x, float y) <br>_Sets the position of the sprite on the screen._  |
|  void | [**setScale**](#function-setscale) (float scaleX, float scaleY) <br>_Sets the scale of the image sprite._  |
|   | [**~ImageManager**](#function-imagemanager) () <br>_Destructs the_ [_**ImageManager**_](classImageManager.md) _instance._ |




























# Detailed Description


The [**ImageManager**](classImageManager.md) class provides a set of methods to manage and display 2D images using SFML. It supports loading images from files, positioning, scaling, and drawing them on the screen via an sf::RenderWindow.




**Note:**

[**ImageManager**](classImageManager.md) assumes the image resources are properly initialized, and the paths provided are valid image file formats supported by SFML. 





    
## Public Attributes Documentation




### variable texture 

_Texture object for storing the image data._ 
```C++
sf::Texture ImageManager::texture;
```



The sf::Texture object holds the image data loaded from a file, which is applied to the sprite for rendering. 


        

<hr>
## Public Functions Documentation




### function ImageManager 

_Constructs an_ [_**ImageManager**_](classImageManager.md) _instance._
```C++
ImageManager::ImageManager () 
```



Initializes the [**ImageManager**](classImageManager.md) to handle image loading and rendering. This constructor prepares the necessary objects for managing images. 


        

<hr>



### function createImage 

_Loads an image from the specified file path._ 
```C++
bool ImageManager::createImage (
    const std::string & filePath
) 
```



Loads an image into an sf::Texture object from the provided file path and applies it to an sf::Sprite for rendering.




**Parameters:**


* `filePath` A string representing the file path of the image. 



**Returns:**

Returns true if the image is successfully loaded, false otherwise. 




**Exception:**


* `std::runtime_error` if the image file cannot be loaded.



**Note:**

Supported image formats include PNG, JPEG, and BMP. 





        

<hr>



### function destroyImage 

_Destroys the image and releases its resources._ 
```C++
void ImageManager::destroyImage () 
```



Cleans up the loaded image and resets the texture and sprite. This is useful for freeing up memory when the image is no longer needed. 


        

<hr>



### function draw 

_Draws the image sprite to the specified render window._ 
```C++
void ImageManager::draw (
    sf::RenderWindow & window
) 
```



Renders the sprite on the provided sf::RenderWindow.




**Parameters:**


* `window` A reference to the sf::RenderWindow where the sprite will be drawn. 




        

<hr>



### function fitToScreen 

```C++
void ImageManager::fitToScreen (
    float windowWidth,
    float windowHeight
) 
```




<hr>



### function getGlobalBounds 

_Gets the global bounding rectangle of the sprite._ 
```C++
sf::FloatRect ImageManager::getGlobalBounds () 
```



Retrieves the boundaries of the sprite in global coordinates, which can be used for collision detection or aligning sprites.




**Returns:**

An sf::FloatRect object representing the global bounding box of the sprite. 





        

<hr>



### function getSprite [1/2]

_Sprite object for rendering the image._ 
```C++
inline sf::Sprite & ImageManager::getSprite () 
```



The sf::Sprite object is used to display the image stored in the texture. It supports transformations such as scaling, rotation, and translation. 


        

<hr>



### function getSprite [2/2]

```C++
inline const sf::Sprite & ImageManager::getSprite () const
```




<hr>



### function setPosition 

_Sets the position of the sprite on the screen._ 
```C++
void ImageManager::setPosition (
    float x,
    float y
) 
```



Adjusts the position of the image sprite to the specified x and y coordinates within the window.




**Parameters:**


* `x` A float representing the x-coordinate of the new position. 
* `y` A float representing the y-coordinate of the new position. 




        

<hr>



### function setScale 

_Sets the scale of the image sprite._ 
```C++
void ImageManager::setScale (
    float scaleX,
    float scaleY
) 
```



Resizes the image sprite by setting its scale factors along the x and y axes.




**Parameters:**


* `scaleX` A float representing the scaling factor along the x-axis. 
* `scaleY` A float representing the scaling factor along the y-axis. 




        

<hr>



### function ~ImageManager 

_Destructs the_ [_**ImageManager**_](classImageManager.md) _instance._
```C++
ImageManager::~ImageManager () 
```



Cleans up any resources used for image handling and rendering, ensuring proper memory deallocation and resource management. 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Image/ImageManager.hpp`

