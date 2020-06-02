---
description: >-
  The Pixy2 camera can do simple object detection and line tracking. Data can be
  communicated to connected devices over I2C, SPI or UART.
---

# Pixy2 Smart Vision Sensor

## About Pixy2

> Pixy2 is smaller, faster and more capable than the original Pixy. Like its predecessor, Pixy2 can learn to detect objects that you teach it, just by pressing a button. Additionally, Pixy2 has new algorithms that detect and track lines for use with line-following robots. The new algorithms can detect intersections and “road signs” as well. The road signs can tell your robot what to do, such as turn left, turn right, slow down, etc. And Pixy2 does all of this at 60 frames-per-second, so your robot can be fast, too.   
> -- [PixyCam homepage](https://pixycam.com/)

Pixy2 is a small camera with an [NXP LPC4330 microcontroller ](https://www.nxp.com/products/processors-and-microcontrollers/arm-microcontrollers/general-purpose-mcus/lpc4300-cortex-m4-m0:MC_1403790133078#/)that is able to do simple object detection and line tracking. It can be connected to all kinds of devices. Its software is available under an opensource license and extensive documentation is available. More information is available on the [PixyCam website](https://pixycam.com/).

## Resources and documentation

The PixyCam website has a [wiki with extensive documentation](https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:start). It includes many guides and tutorials and additional information for using the Pixy2. Make sure that you are using the Pixy2 documentation, not the documentation for previous version of the Pixy.

## Using Pixy2 with PX4

A basic port of the Pixy library for Arduino was made for PX4/NuttX. This code allows you to connect the Pixy2 through I2C or SPI to the FMUK66. It provides a simple interface to access the data coming from the Pixy2 in your own PX4 modules.

The code is available under the NXP HoverGames GitHub:

{% embed url="https://github.com/NXPHoverGames/PixyCam" %}



