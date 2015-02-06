# AUDIO-BIT-TWIDDLING
A list of audio sample manipulations. Using bitwise operators where possible. Contributions welcome!  
##reducing bitdepth
Go ahead and chop that extra resolution right off. If we were going the other way, we'd need to add dithering.
```c
int16_t PCM16bit = PCM24bit >> 8;
```
