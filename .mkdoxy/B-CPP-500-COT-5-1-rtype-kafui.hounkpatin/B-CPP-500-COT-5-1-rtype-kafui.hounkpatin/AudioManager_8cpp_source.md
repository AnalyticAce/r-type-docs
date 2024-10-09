

# File AudioManager.cpp

[**File List**](files.md) **>** [**Audio**](dir_f379be214ac3ab501d342456492bfadc.md) **>** [**AudioManager.cpp**](AudioManager_8cpp.md)

[Go to the documentation of this file](AudioManager_8cpp.md)


```C++
#include "../../../include/Engine/Audio/AudioManager.hpp"

AudioManager::AudioManager() {}

AudioManager::~AudioManager() {}

void AudioManager::playSound(const std::string &Path) {
  if (!buffer.loadFromFile(Path)) {
    std::cout << "Error loading sound" << std::endl;
  }
  sound.setBuffer(buffer);
  sound.play();
}

void AudioManager::playMusic(const std::string &Path) {
  if (!music.openFromFile(Path)) {
    std::cerr << "Error loading music from " << Path << std::endl;
    return;
  }
  music.play();
  music.setLoop(true);
}

void AudioManager::pauseMusic() { music.pause(); }

void AudioManager::resumeMusic() { music.play(); }

void AudioManager::setMusicVolume(float volume) { music.setVolume(volume); }

void AudioManager::setSoundVolume(float volume) { sound.setVolume(volume); }

void AudioManager::setPitch(float pitch) { sound.setPitch(pitch); }
```


