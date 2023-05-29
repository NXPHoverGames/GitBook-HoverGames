# Panasonic AMG8833 IR sensor

## Installing the sensor

The datasheet of the AMG8833 you can find [here](http://www.farnell.com/datasheets/2058257.pdf?\_ga=2.187765294.767814663.1555052764-1882353189.1555052764). You can connect the sensor with the "I2C/NFC" connector on the FMU. To mount the sensor, you can solder 5x1 jacks to a breadboard so the sensor can be placed on the board. On the back of the breadboard you can solder the cables for the FMU plug according to the label on the sensor. For the power supply use the connector "VIN". You just need to solder the cables at the lower row. The upper row is just for a stable assembly. The end of the cable has to be plugged into the FMU plug as shown below.

![](<../.gitbook/assets/amg88xx\_pinconnection (1).png>)

## Example Code

Example code for using the MLX90614 under PX4 is available under the NXP HoverGames GitHub:

{% embed url="https://github.com/NXPHoverGames/ThermoCam" %}

The example was written in C++ and bases on the "px4\_simple\_app" in the examples folder of the PX4 Firmware. You can find the example in the folder "hg\_amg88xx" and includes the files "CMakeLists.txt", "hg\_amg88xx.h" and "hg\_amg88xx.cpp".

For running the example the command `hg_amg88xx` has to be added under the keyword "EXAMPLES" in the file "_default.cmake"_  from the folder "_.../src/Firmware/boards/nxp/fmuk66-v3" ._ Also copy the folder "hg\_amg88xx" in the folder "_.../src/Firmware/src/examples"._

```cpp
HG_AMG88xx temp_amg;
float pixels[AMG88xx_PIXEL_ARRAY_SIZE];

temp_amg.readPixels(pixels, AMG88xx_PIXEL_ARRAY_SIZE);
```

First creating an object of the "HG\_AMG88xx"-Class. Then you can call the `readPixels(float *buf, uint8_t size)` for reading the actual temperature of all 64 pixels. Then you can print every pixel using a for-loop.
