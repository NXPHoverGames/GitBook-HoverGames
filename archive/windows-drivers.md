---
description: >-
  How to modify and install the Windows drivers for the RDDRONE-FMUK66 and
  telemetry radio module.
---

# Windows drivers

## USB drivers for RDDRONE-FMUK66

{% hint style="success" %}
This is a temporary issue and should be resolved as updates are made to the QGroundControl package installer. 
{% endhint %}

QGroundControl will install all needed drivers to connect the flight controller, but the drivers might not yet be updated for the RDDRONE-FMUK66. When you plug in the FMU board after the installation of QGroundControl and Windows notifies you that no driver was found for this hardware, you have to modify the drivers.

To update the drivers, make a copy of the `C:\Program Files (x86)\px4 driver\Drivers` folder to another location. Then, go to `Control Panel > Programs > Uninstall a program`. There, uninstall the following drivers that were installed with QGroundControl:

* px4 driver
* Windows Driver Package - 3D Robotics \(usbser\) Ports  \(04/11/2013 2.0.0.4\)
* Windows Driver Package - Arduino LLC \(www.arduino.cc\) \(usbser\) Ports  \(11/15/2012 5.1.2600.1\)
* Windows Driver Package - FTDI CDM Driver Package - Bus/D2XX Driver \(07/12/2013 2.08.30\)
* Windows Driver Package - FTDI CDM Driver Package - VCP Driver \(07/12/2013 2.08.30\)

In the copied driver folder, edit`px4fmu.inf` to include the following vendor and product ID definitions in both lists \(`DeviceList` and `DeviceList.NTamd64`\):

```text
USB\VID_26AC&PID_1001, USB\VID_26AC&PID_006E, USB\VID_1FC9&PID_001C
```

Now the `DPinstx64.exe` executable can be used to reinstall the drivers. Note that on a 32 bit system, you will need to use the`DPinstx86.exe` executable.

{% hint style="warning" %}
The installer might give a warning about unknown or unsigned drivers. That happens because you just modified the driver. It should be completely safe to disregard the warning and continue the install process.
{% endhint %}

## USB drivers for telemetry radio

If the driver for the telemetry radio is not automatically being installed after connecting it using USB, you will have to manually install these Virtual COM Port drivers. A link is provided on the [downloads page](../downloads.md#virtual-com-port-drivers-for-ftdi-usb-ttl-3-v3-cable).

