---
description: Accessing and using the PX4 system console.
---

# PX4 system console

There are different options to connect to the serial console of the FMU. The most direct one is the connection with the debug breakout board and FTDI cable. Any serial connection program can be used. On Linux systems Minicom is widely used, on Windows Tera Term or Putty can be used. Main factor here is to set the baudrate correctly. While most systems use 115200 baud as the default, **the RDDRONE-FMUK66 uses 57600 baud**. 8 Bit, no parity, is pretty much common.

The system console can also be accessed from QGroundControl, but only when the system has completely booted and a connection between the FMU and QGroundControl can be established. It is called MAVLink Console, and it is available in the same menu as the log downloads.

![The MAVLink Console can be found in the same menu as the Log Download feature. ](../../.gitbook/assets/image%20%2887%29.png)

More information about the system console is available on the PX4 Developer Guide:

{% embed url="https://dev.px4.io/en/debug/system\_console.html" %}

