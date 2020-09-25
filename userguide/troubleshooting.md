---
description: >-
  This page lists some frequently asked questions and problems that often occur,
  and how to solve these issues. Please have a look at this page before you ask
  for help in the community.
---

# Troubleshooting

## Switching the device off and on

Many problems are solved by simply switching the device off and on. This goes for both the RDDRONE-FMUK66 and your computer. If you can't connect with your drone, first try to switch it on and off, and also try restarting the software you are using, or reboot your PC.

## Unable to make connection from Windows computer to FMU

There are still issues with the Windows driver that comes with QGroundControl. It does not yet recognize and support the RDDRONE-FMUK66. It is possible to modify the driver yourself to get it to work, but this does not seem to solve the issue completely. Flashing firmware might still be impossible.

{% page-ref page="../archive/windows-drivers.md" %}

Flashing firmware using the debugger should always work, even under Windows. Otherwise, it might be a good idea to setup a virtual machine with a Linux OS. The Linux version of QGroundControl does recognize the FMU, and this also works in a virtual machine if you set up the USB passthrough correctly. Note that the FMU has a bootloader which is seen as a seperate device during boot, you will also have to add this device.

## The FMU is not booting

Make sure there is a bootloader on the board, and that the firmware is working correctly. Try to rewrite both the bootloader and firmware using the debugger.

{% page-ref page="programming.md" %}

{% page-ref page="qgroundcontrol/firmware.md" %}

## The FMU is not receiving power through its USB port

Check if you can power the FMU at all. If the FMU works fine when the battery is connected, but not when only USB is connected, it could be that fuse F3 is blown. Please see the page about the fuses on the RDDRONE-FMUK66 board.

{% page-ref page="../rddrone-fmuk66/electrical-fuses.md" %}

## ESC calibration does not work or motors don't work properly

If the motors are not spinning at the right speed, or are not reacting properly to changes in the throttle input coming from the controller, there are quite a few things to check.

Check the electrical connections, see if the bullet connectors coming from the motors are completely plugged into the ESCs, and check if the ESCs are soldered in the right way and if they receive power.

{% hint style="danger" %}
The three bullet connectors coming from the motor have a piece of heat shrink tubing over them. Sometimes, the glue from this heat shrink tubing is also on the part of the connector that goes into the ESC. It should be visible, but it will also be clear when you need a lot of force to get the connector into the ESC. If this is the case, make sure to wipe of the glue. You might need to use some alcohol. If you don't do this, it might cause connection issues.
{% endhint %}

On the software side, you can redo [ESC calibration](qgroundcontrol/power.md#esc-calibration) to make sure that the ESCs are properly responding to input from the FMU. 

Also make sure to check your RC configuration on both the transmitter \(controller\) and the FMU. Also check with the information in the radio tab in QGroundControl if the signal is properly received.

If you cannot solve the issue yourself, try to determine whether the source of the issue is electrical or due to the software, and [ask for help in the community or contact the HoverGames team](../contact.md).

## Testing the PWM output, ESC, motors manually 

{% hint style="danger" %}
**DANGER** - **REMOVE** the propellers!

This method bypasses some of the internal failsafes!
{% endhint %}

The airframe must be set, and to get accurate results the motor calibration should be completed. **After ensuring the propellers are removed for safety**, from the console you can issue the following commands to directly test and exercise the PWM outputs:

* The fmu test command will sweep all the PWMS up and down repeatedly

`>fmu test`

* The pwm command will let you individually control the pwm output channels as configured by your specific airframe and mixer settings.

`>pwm test -c 1234 -p 1300`

`>pwm -test -c 24 -p 1630`

You can use the -c parameter to select which channels you want to use. With the -p parameter you can select the pwm value.

## Unable to establish a MAVLink v2 connection in some cases

It was reported that MAVLink v2 is not always used when it should. By default, PX4 uses MAVLink v1, unless v2 is supported and requested to be used by the connected device. 

A possible solution is to set the `MAV_PROTO_VER` parameter to `2`, to force all MAVLink connections to use MAVLink v2. Note that this makes it impossible to use devices that only support MAVLink v1!

## Vibration management and improvement

{% embed url="https://youtu.be/RGaxJYsERkw" %}



## Unable to solve your problem?

If you question is not answered on this page, or you are not able to solve the problem yourself, first try to ask in the community \(if applicable\). Otherwise, [contact the HoverGames team](../contact.md).

