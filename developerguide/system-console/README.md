---
description: Accessing and using the PX4 system console.
---

# PX4 system console

There are different options to connect to the serial console of the FMU. The most direct one is the connection with the DCD-LZ debug breakout board and FTDI cable. This is known as the root console and is initialized and starts emitting data immediately on power up or after reset. This can help specifically with lower level debugging. Any of the typical serial connection programs can be used. On Linux systems Minicom is widely used, on Windows TeraTerm or Putty can be used. Main detail to be careful of is to ensure the baudrate is set correctly. While many systems use 115200 baud as the default, **the RDDRONE-FMUK66 uses 57600 baud**. 8 Bit, no parity, is generally used.

Typically it is convenient to use the system console can also be accessed from QGroundControl. This assumes the system has successfully completed boot up and a connection between the FMU and QGroundControl can be established. It is called MAVLink Console, and it is available in the same menu as the log downloads. The MAVLink Console is available over both a hardwired USB cable connection and wirelessly over a telemetry connection.

![The MAVLink Console can be found in the same menu as the Log Download feature. ](<../../.gitbook/assets/image (78).png>)

More information about the system console is available on the PX4 Developer Guide:

{% embed url="https://dev.px4.io/en/debug/system_console.html" %}
