# AUDIO-BIT-TWIDDLING
A collection of audio sample manipulations; using bitwise operators where possible. Contributions welcome!  
##reducing bitdepth
Go ahead and chop that extra resolution right off. If we were going the other way, we'd need to add dithering.
```c
int16_t PCM16bit = PCM24bit >> 8;
```
##unsigned PCM to signed PCM.
This example uses a 24-bit sample.
```c
if (PCM24bit & 0x800000) PCM24bit |= ~0xffffff;
//0x800000 equals (2 ^ (24 - 1))
//0xffffff equals (2 ^ 24)
```
