

# File AudioManager.hpp

[**File List**](files.md) **>** [**Audio**](dir_c82188eaffb96b2487ed13b79df10c60.md) **>** [**AudioManager.hpp**](AudioManager_8hpp.md)

[Go to the documentation of this file](AudioManager_8hpp.md)


```C++
#ifndef AUDIO_MANAGER_HPP
#define AUDIO_MANAGER_HPP

#include <SFML/Audio.hpp>
#include <iostream>

class AudioManager {
private:
  sf::SoundBuffer buffer;

  sf::Sound sound;

  sf::Music music;

public:
  AudioManager();

  ~AudioManager();

  void playSound(const std::string &Path);

  void playMusic(const std::string &Path);

  void pauseMusic();

  void resumeMusic();

  void setMusicVolume(float volume = 100);

  void setSoundVolume(float volume = 100);

  void setPitch(float pitch = 1.0);
};

#endif // AUDIO_MANAGER_HPP
```


