# AUDIO-BIT-TWIDDLING
A collection of audio sample manipulations; using bitwise operators where applicable. Examples are in C, and contributions are welcome.

##increasing bitdepth
For audio processing, there's no real reason to do this. There won't be any quantization distortion when going from a smaller bitdepth to a larger bitdepth, so we won't need to add dither.
```c
int32_t PCM24bit = PCM16bit << 8;
```

##reducing bitdepth
Go ahead and chop that extra resolution right off. This is called truncation. We should really be adding <a href = "http://en.wikipedia.org/wiki/Dither#Digital_audio">dither</a> when going from a larger bitdepth to a smaller bitdepth, though. 
```c
int16_t PCM16bit = PCM24bit >> 8;
```

##unsigned PCM to signed PCM
This example uses a 24-bit sample.
```c
if (PCM24bit & 0x800000) PCM24bit |= ~0xffffff;
//0x800000 == (2 ^ (24 - 1))
//0xffffff == (2 ^ 24)
```

##signed PCM to floating point PCM
This example uses a 24-bit sample.
```c
double sampleFloat = (PCM24bit * (1.0 / 0x7fffff));
//0x7fffff == (2 ^ (24 - 1)) - 1
```
