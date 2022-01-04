---
description: >-
  This page lists some useful NuttX console commands. You can access the console
  through QGroundControl or using a USB-TTL-3V3 cable and debugger adapter
  board.
---

# Useful console commands

## PX4 Dev Guide commands reference

The PX4 Dev Guide provides an auto-generated overview of (almost) all available commands. See the following page in the Dev Guide:

{% embed url="https://dev.px4.io/en/middleware/modules_main.html" %}

This page should provide an overview of some important and useful commands that people participating in the HoverGames might find useful.

{% hint style="info" %}
This page will be updated when we come accross more useful commands. suggested improvements are welcome via email at HoverGames@nxp.com or [https://community.nxp.com/community/mobilerobotics](https://community.nxp.com/community/mobilerobotics)&#x20;
{% endhint %}

## Test SDcard operation

You can perform a test of how well the currently inserted SD card is performing using the `sd_bench` command.

## Test flash memory operation and erase flash memory

You can perform a read/write test of the flash memory using the `mtd rwtest` command.

The part of the flash memory which holds all PX4 parameters can be erased using the `mtd erase` command.&#x20;

{% hint style="warning" %}
`mtd_erase` may be useful when you have flashed new firmware and find the need to do a full reset of the PX4 settings and parameters.
{% endhint %}

## Start drivers for the available sensors on RDDRONE-FMUK66

All sensor drivers should be started on startup, but if this does not work or when you are debugging and need to restart a driver, you can use the following commands

NXP MPL3115A2 pressure sensor (I2C): `mpl3115a2 -I start`\
NXP FXOS8701CQ accelerometer/magetometer (SPI): `fxos8701cq start -a 8 -R 0`\
NXP FXAS21002C gyroscope (SPI): `fxas21002c start -R 0`

The file that starts the sensors on power up and specifies which bus it is connected to, is located at`ROMFS/px4fmu_common/init.d/rc.sensors`

{% code title="ROMFS/px4fmu_common/init.d/rc.sensors" %}
```
if ver hwcmp NXPHLITE_V3
then
        # Internal I2C (baro)
        mpl3115a2 -I start

        # Internal SPI (accel + mag)
        fxos8701cq start -a 8 -R 0

        # Internal SPI (gyro)
        fxas21002c start -R 0
fi
```
{% endcode %}

## Sensor commands

Each sensor has a set of commands, which are usually presented when you enter the name of the sensor without a specific command. For example, `fxos8701cq` supports the following commands:

```
fxos8701cq start
fxos8701cq stop
fxos8701cq test
fxos8701cq reset
fxos8701cq info
fxos8701cq testerror
fxos8701cq regdump
```

## Set and view parameter settings from command line

Parameters can be set from the command line, using `param set PARAM VALUE`, where PARAM is the name of the parameter and VALUE is the value to which it should be set.

For example, the airframe parameters can be set using`param set SYS_AUTOSTART 4014`, which sets the airframe to S500. After a reboot, the SYS\_AUTOSTART parameter will then also change other parameters to the values that are set within the S500 airframe definition.

You can also easily read the current value a parameter is set to with`param show PARAM`. This also allows for wildcard characters. For example, if you want to show the values of all parameters that start with SYS, you can use `param show SYS*`.

## MAVLink instances

You can see the current active MAVLink instances using `mavlink status`

## Listening to uORB messages

PX4 uses uORB for its internal communication between modules. It is possible to listen to uORB topics, which can be very useful for debugging or when developing new functions. See the following page for more information and commands:

{% embed url="https://dev.px4.io/en/middleware/uorb.html#listing-topics-and-listening-in" %}
