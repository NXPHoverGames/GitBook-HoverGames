---
description: >-
  Using a companion computer is a straightforward way to extend the
  functionality of your drone by running some of your own software.
---

# Companion computers

## Onboard computer or wireless link?

The 915/433 MHz telemetry radios provided with the KIT-HGDRONEK66 kit, allows control of the HoverGames drone from a personal computer. You may be able to send enough data back and forth to have a program on your ground based PC to control the drone live. An additional, and typically better way to control the drone is by having a small onboard computer that connects directly to the FMU. This opens up the world of onboard and autonomous processing without relying on the radio connection, speed or bandwidth. 

Some applications may even be able to make use of both a ground based computer and an on board companion computer. For example in search and rescue operations, an onboard companion computer may be able to pick out key sections of video of interest - which have some "anomaly", compress the video file, and send only those video snippets of interest to a more powerful ground computer to analyse the images in more detail.

An onboard companion computer running Linux also makes deploying these programs and using modern communications technology such as cellular or other IP radio systems easier. It is also may be possible to safely update on the fly the activity of a Linux companion computer than if you were trying to do the same with the embedded FMU that is responsible for the real time task of keeping the drone flying.

## Hardware interfaces to a companion computer

The PX4 Developer Guide has a page dedicated to the use of companion computers.

{% embed url="https://dev.px4.io/master/en/companion\_computer/pixhawk\_companion.html" %}

In many cases, the companion computer communicates to the FMU via a direct UART to UART connection. A connection may able be made via a set of radio transceivers, which would also normally connect to a serial port. The FMUK66 has multiple UARTs exposed, and the easiest ones to use are the TELEM1 and TELEM2 ports.

{% hint style="info" %}
PX4 currently only supports communication with a companion computer over serial \(UART\). CAN, SPI and I2C are **not** supported for this purpose and there are currently no plans to introduce companion link support on any of these buses.

IP based connections via 100BaseT1 "2-wire" Ethernet is a desirable connection type, and we can expect to see PX4 enablement in that area soon. 

There is also development on UAVCAN V1 - it is possible a connection may be enabled in the future.
{% endhint %}

When adding a companion computer on the drone itself, on the FMUK66 normally TELEM2 is used to connect it. TELEM1 would remain reserved for your telemetry link to QGroundControl. How to configure these serial ports for different applications is explained in the PX4 User Guide. In most cases you want the highest possible baudrate for the link to your companion computer \(921k\).

{% embed url="https://docs.px4.io/v1.9.0/en/peripherals/serial\_configuration.html" %}



## Software communications between companion computer and FMU

Once the physical connection is determined there are still several software methods to choose from of communicating between the Companion Computer and the FMU.

### MAVSDK

MAVSDK is one of the easiest way to communicate with the FMU from your companion computer. The MAVSDK guide states_"The library provides a simple API for managing one or more vehicles, providing programmatic access to vehicle information and telemetry, and control over missions, movement and other operations"_. MAVSDK supports C++, Swift and Python, and support for other programming languages is in development. 

MAVSDK has its own GitBook with some examples and an API reference.

{% embed url="https://mavsdk.mavlink.io/develop/en/index.html" %}

## Using ROS or ROS2: MAVROS and px4\_ros\_com

A more advanced, and commonly used option for controlling your drone using a companion computer is to use ROS \(Robot Operating System\) to develop your application. ROS is far beyond the scope of this GitBook, further information and documentation is available on the ROS.org website. It is worth studying further once you understand PX4 fundamentals.

{% embed url="https://www.ros.org/" %}

You can use either the original ROS or ROS2. For the original ROS, a package called MAVROS is available which acts as a bridge between MAVLink and ROS.

{% embed url="https://dev.px4.io/master/en/ros/mavros\_installation.html" %}

For ROS2, the px4\_ros\_com package is available. PX4 includes a FastRTPS bridge between uORB and RTPS. RTPS is used as the middleware for ROS2.   
  
It is worth noting that ROS and ROS2 as well as these publish/subcribe concepts are a popular, versatile and modern programming methods and is worthwhile studying further. More information is available in the PX4 Dev Guide here:

{% embed url="https://dev.px4.io/master/en/middleware/micrortps.html" %}



