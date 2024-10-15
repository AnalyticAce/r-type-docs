

# Class AudioManager



[**ClassList**](annotated.md) **>** [**AudioManager**](classAudioManager.md)



_Handles sound and music playback using the SFML audio library._ [More...](#detailed-description)

* `#include <AudioManager.hpp>`





































## Public Functions

| Type | Name |
| ---: | :--- |
|   | [**AudioManager**](#function-audiomanager) () <br>_Constructs an_ [_**AudioManager**_](classAudioManager.md) _instance._ |
|  void | [**pauseMusic**](#function-pausemusic) () <br>_Pauses the currently playing music._  |
|  void | [**playMusic**](#function-playmusic) (const std::string & Path) <br>_Plays a music track from a specified file._  |
|  void | [**playSound**](#function-playsound) (const std::string & Path) <br>_Plays a sound effect from a specified file._  |
|  void | [**resumeMusic**](#function-resumemusic) () <br>_Resumes music playback from the paused position._  |
|  void | [**setMusicVolume**](#function-setmusicvolume) (float volume=100) <br>_Sets the volume level for music playback._  |
|  void | [**setPitch**](#function-setpitch) (float pitch=1.0) <br>_Adjusts the pitch of the sound effect._  |
|  void | [**setSoundVolume**](#function-setsoundvolume) (float volume=100) <br>_Sets the volume level for sound effects playback._  |
|   | [**~AudioManager**](#function-audiomanager) () <br>_Destructs the_ [_**AudioManager**_](classAudioManager.md) _instance._ |




























# Detailed Description


The [**AudioManager**](classAudioManager.md) class provides a comprehensive interface for managing and controlling audio playback in an application. It supports both short sound effects via sf::Sound and longer music tracks via sf::Music, offering functionality for loading, playing, pausing, resuming, and adjusting audio properties such as volume and pitch.


This class is implemented as a singleton to ensure centralized audio management and prevent multiple instances from causing resource conflicts or duplicate sound playback.




**Note:**

[**AudioManager**](classAudioManager.md) assumes the audio resources are properly initialized, and the paths provided are valid audio file formats supported by SFML. 





    
## Public Functions Documentation




### function AudioManager 

_Constructs an_ [_**AudioManager**_](classAudioManager.md) _instance._
```C++
AudioManager::AudioManager () 
```



Initializes the [**AudioManager**](classAudioManager.md) for managing sound and music playback. In a full singleton implementation, this constructor should be private, and a static method would control instance creation. 


        

<hr>



### function pauseMusic 

_Pauses the currently playing music._ 
```C++
void AudioManager::pauseMusic () 
```



Temporarily halts music playback, preserving the current position. This allows the music to be resumed from the same point using [**resumeMusic()**](classAudioManager.md#function-resumemusic).




**Note:**

This function only affects music playback and not sound effects. 





        

<hr>



### function playMusic 

_Plays a music track from a specified file._ 
```C++
void AudioManager::playMusic (
    const std::string & Path
) 
```



Loads and streams music from the given file path, starting playback once the music file is successfully opened. Music files should be larger audio tracks intended for extended playback.




**Parameters:**


* `Path` A string representing the file path of the music track. 



**Exception:**


* `std::runtime_error` if the music file cannot be opened.



**Note:**

Supported music formats include OGG, FLAC, MP3 and WAV. 





        

<hr>



### function playSound 

_Plays a sound effect from a specified file._ 
```C++
void AudioManager::playSound (
    const std::string & Path
) 
```



Loads a sound from the provided file path into the buffer and immediately plays it using the sf::Sound object.




**Parameters:**


* `Path` A string representing the file path of the sound effect. 



**Exception:**


* `std::runtime_error` if the sound file cannot be loaded.



**Note:**

Ensure the sound file is in a supported format (e.g., WAV, OGG, MP3). 





        

<hr>



### function resumeMusic 

_Resumes music playback from the paused position._ 
```C++
void AudioManager::resumeMusic () 
```



Continues playing the previously paused music from the exact position it was paused.




**Note:**

Music must have been paused using [**pauseMusic()**](classAudioManager.md#function-pausemusic) for this method to work. 





        

<hr>



### function setMusicVolume 

_Sets the volume level for music playback._ 
```C++
void AudioManager::setMusicVolume (
    float volume=100
) 
```



Adjusts the volume for the music being played. The volume is a floating-point value between 0 (mute) and 100 (full volume).




**Parameters:**


* `volume` A float representing the desired volume level (default is 100).



**Note:**

This function only affects the music volume, not sound effects. 





        

<hr>



### function setPitch 

_Adjusts the pitch of the sound effect._ 
```C++
void AudioManager::setPitch (
    float pitch=1.0
) 
```



Sets the pitch for the sound effect currently loaded into the sf::Sound object. The pitch determines how high or low the sound is played, with a value of 1.0 being the normal pitch.




**Parameters:**


* `pitch` A float representing the desired pitch level (default is 1.0).



**Note:**

This function only affects sound effects, not music. 





        

<hr>



### function setSoundVolume 

_Sets the volume level for sound effects playback._ 
```C++
void AudioManager::setSoundVolume (
    float volume=100
) 
```



Adjusts the volume of the sound effects being played. The volume is a floating-point value between 0 (mute) and 100 (full volume).




**Parameters:**


* `volume` A float representing the desired volume level (default is 100).



**Note:**

This function only affects sound effects volume, not music. 





        

<hr>



### function ~AudioManager 

_Destructs the_ [_**AudioManager**_](classAudioManager.md) _instance._
```C++
AudioManager::~AudioManager () 
```



Cleans up and releases any audio resources associated with sound or music playback, ensuring proper resource deallocation. 


        

<hr>

------------------------------
The documentation for this class was generated from the following file `include/Engine/Audio/AudioManager.hpp`

