---
description: >-
  During the development of the RDDRONE-FMUK66 (NXPhlite) several hardware
  issues were discovered and fixed in newer revisions. Boards send to HoverGames
  participants should NOT have these issues.
---

# Hardware errata

## NXPhlite Rev. C - Replace buffer U50 with a resistorpack

Bi-directional buffer U50 was found to oscillate when UART4 is set to higher baudrates, or when long cables are connected to the TELEM1 connector. As a solution, the U50 levelshifter was removed from the board and a 220R resistor pack was placed in parallel.

## NXPhlite Rev. C - Servorail PWM1 GND not connected

The GND pin of the PWM1 connector on the PWM servorail was left floating. This might cause distortion of the PWM signal that goes to the ESC. As a quick solution, the PWM1 GND can be soldered to the PWM2 GND (which is correctly connected to the ground plane).

## NXPhlite Rev. A - Buffer U50 oscillates due to a 5V output level instead of the expected 3V3

The team has discovered that the auto-sensing bi-directional buffer part U50 is configured for 5V signalling. This is causing the lines to oscillate when connected to the 3V3 signalling on the typical SiK telemetry radios used. The solution is to either remove U50, or connect the "B" side of the buffer to 3V instead of 5V. This is precision work and very difficult to do by hand. It will be corrected in the next revision. If you are unable to get this done yourself, please contact Iain Galloway or Matthias Wilkens to arrange a reworked replacement board.

![Not so nice rework of U50: Cut and jumper VCCB to 3V3.](<../.gitbook/assets/image (10).png>)

![Alternative: Removing and jumpering U50 - Very difficult to do by hand.](<../.gitbook/assets/image (12).png>)

## Debug breakout board Rev. A - FTDI cable should not supply power to the debugger and FMU board

The first prototype version V01 / Rev. A of the DCD-LZ-ADAPT needs small rework in order to allow the J-Link debugger and the FTDI cable to work simultaneously.

* The FTDI cable supplies 5V on VCC, and this causes the J-Link debugger to think the board is in reset.
* VCC from the processor needs to appear on pin 1 of the SWD header.

![](../.gitbook/assets/DCD-LZ-ADAPT\_Rework.png)

## NXPhlite early boards - Oscillator installed upside down

The first build of boards had the oscillator Y1 installed upside down. The markings on this part are a little challenging based on the datasheet and the actual visibility on the part. The images below should help clarify how it is to be installed.

![](<../.gitbook/assets/Oscillator Y1 wrong.png>)

![](../.gitbook/assets/OscillatorY1\_correct.png)

### Oscillator schematic

![](../.gitbook/assets/Oscillator\_schematic.png)

