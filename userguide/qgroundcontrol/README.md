---
description: >-
  This section will explain how to configure the PX4 software running on the
  RDDRONE-FMUK66.
---

# PX4 configuration using QGroundControl

## QGroundControl

Ground control software is used for configuration and monitoring of your drone. We will use [QGroundControl](http://qgroundcontrol.com/) to configure the PX4 flight stack that you should have been programmed on your FMU. With QGroundControl you can configure the propeller configuration, radio controller, sensor calibration and much more. It also provides different ways of controlling the drone, such as an autonomous mission planner. Download links for QGroundControl are available on the [downloads page](../../downloads.md#qgroundcontrol).

The next sections will guide you through the process of using QGroundControl to set up your FMU. All the steps correspond to one setup screen inside of QGroundControl. In the QGroundControl documentation you can find more information about each of these steps.

At the top of the next few sections there will be a link to the corresponding page of the QGroundControl User Guide. Each section will also have additional information specific to RDDRONE-FMUK66 and HoverGames. This distribution was chosen to make sure that we are not mirroring the official QGroundControl documentation too much.

{% embed url="https://docs.qgroundcontrol.com/en/SetupView/SetupView.html" %}

## Connect your FMU to QGroundControl

In order to configure your FMU through QGroundControl, you need to connect it to a computer that has QGroundControl installed on it. This can be done directly with a micro-USB to regular USB cable, or with the telemetry radio transceiver set that you bought together with the HoverGames drone kit. On the FMU side, the telemetry radio transceiver can be connected to the TELEM connector, while the computer side has a USB-A connector which can be plugged in directly. Both these links should be automatically detected by QGroundControl. The differences can be found in the table below:

| Property | USB cable | Telemetry radio |
| :--- | :--- | :--- |
| Connection type | Wired | Wireless |
| Link speed | Very fast | Slow |
| Can upgrade firmware | Yes | No |
| Can perform ESC calibration | Yes | No |
| Can be used mid-flight | No\* | Yes |

{% hint style="info" %}
\(\*\) While the USB connection cannot be used to connect the FMU to a laptop mid-flight, it can be used as a way to connect a companion computer for performing complex computations on the drone. This requires advanced parameter configuration \(one step required is [disabling the USB link check circuit breaker](https://dev.px4.io/en/advanced/parameter_reference.html#CBRK_USB_CHK)\).
{% endhint %}



