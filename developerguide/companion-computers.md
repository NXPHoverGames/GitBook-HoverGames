---
description: >-
  Using a companion computer is a straightforward way to extend the
  functionality of your drone by running some of your own software.
---

# Companion computers

## Onboard computer or wireless link?

Some people are using the 915/433 MHz telemetry radios to control their drone from their personal computer, instead of having a small onboard computer that connects directly to the FMU. This might work, but the latency might be too high and/or the bandwidth may be too low. It depends on your application if you need a reliable link between the FMU and the companion computer.

## Setup a companion computer

The PX4 Developer Guide has a page dedicated to the use of companion computers.

{% embed url="https://dev.px4.io/master/en/companion\_computer/pixhawk\_companion.html" %}

In most cases, the companion computer communicates to the FMU via UART. Or via a set of radio transceivers, which also connects to a serial port. The FMUK66 has multiple UARTs exposed, but the easiest ones to use are the TELEM1 and TELEM2 ports.

{% hint style="info" %}
PX4 \(currently\) only supports communication with a companion computer over serial \(UART\). CAN, SPI and I2C are NOT supported for this purpose and there are currently no plans to introduce companion link support on any of these buses.
{% endhint %}

If you are putting a companion computer on the drone itself, you would normally use TELEM2 to connect it. In that case, TELEM1 is usually reserved for your telemetry link to QGroundControl. How to configure these serial ports for different applications is explained in the PX4 User Guide. In most cases you want the highest possible baudrate for the link to your companion computer \(921k\).

{% embed url="https://docs.px4.io/v1.9.0/en/peripherals/serial\_configuration.html" %}

## MAVSDK

The MAVSDK is the easiest way to comunicate with the FMU from your companion computer. You can already use C++, Swift and Python with it, and support for other programming languages is being worked on. MAVSDK has its own GitBook with some examples and an API reference.

{% embed url="https://mavsdk.mavlink.io/develop/en/index.html" %}

## Using ROS\(2\): MAVROS and px4\_ros\_com

A more advanced option would be to use ROS \(Robot Operating System\) to develop your application. ROS is far beyond the scope of this GitBook, further information and documentation is available on the ROS.org website.

{% embed url="https://www.ros.org/" %}

You can use either the original ROS or ROS2. For the original ROS, a package called MAVROS is available which acts as a bridge between MAVLink and ROS.

{% embed url="https://dev.px4.io/master/en/ros/mavros\_installation.html" %}

For ROS2, the px4\_ros\_com package is available. PX4 includes a FastRTPS bridge between uORB and RTPS. RTPS is used as  the middleware for ROS2. Further information is available in the PX4 Dev Guide:

{% embed url="https://dev.px4.io/master/en/middleware/micrortps.html" %}



