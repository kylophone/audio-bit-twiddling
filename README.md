# AUDIO-BIT-TWIDDLING
A collection of audio sample manipulations; using bitwise operators where applicable. Examples are in C, and contributions are welcome.

##increasing bitdepth
You won't be gaining any resolution here, and your samples will be larger. To avoid quantization distortion, we should also be adding dither here.
```c
int32_t PCM24bit = PCM16bit << 8;
```

##reducing bitdepth
Go ahead and chop that extra resolution right off. This is called truncation. To avoid quantization distortion, we should also be adding dither here.
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
