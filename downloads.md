---
description: An overview of useful software packages.
---

# Downloads

## Preconfigured virtual machine image with development tools

* [Download preconfigured virtual machine image](https://s3-us-west-2.amazonaws.com/hovergames/Hovergames-VM-2019-04-08.ova) (Courtesy of Dronecode)
* [Download Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)

A preconfigured Ubuntu Linux virtual machine image for [Oracle VM VirtualBox](https://www.virtualbox.org) is available for download courtesy Dronecode. The image includes the tools for editing, building and debugging software for the RDDRONE-FMUK66 and other HoverGames hardware.&#x20;

More information and instructions are available in our [Developer Guide](developerguide/tools/), including instructions on how to setup your own virtual machine from scratch. It is recommended to have a look at these pages, and adapt some of the default settings to add more RAM and CPU cores to your VM if your hardware is powerful enough.

{% hint style="info" %}
The user account _hovergames_ also has _hovergames_ as its password! Under Ubuntu, there is no root account by default, but the _hovergames_ user account has root privileges. Use `sudo` __ before a command to run it as root or use `sudo su` to gain root privileges.
{% endhint %}

{% hint style="warning" %}
There is an Extension Pack available for VirtualBox which includes support for USB 2.0 and USB 3.0 devices. It is not required, but it might be useful to also install this Extension Pack.

While the basic VirtualBox software is available free of charge for all users, the VirtualBox Extension Pack is only licensed free for **personal use**. [Commercial users have to pay for a license](https://www.virtualbox.org/wiki/Licensing\_FAQ). Employees of NXP Semiconductors or other organizations should check with their IT departments for licence costs.
{% endhint %}

## PX4 Autopilot builds for RDDRONE-FMUK66

(Note: NXP does not provide precompiled code. Binaries courtesy of PX4.io)

* [Download nxp\_fmuk66-v3\_default.px4](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.px4) (**stable** build, **recommended**, for use with **QGroundControl**)
* [Download nxp\_fmuk66-v3.bin](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3.bin) (**stable** build, **recommended**, for use with **J-Link Commander**)
* [Download nxp\_fmuk66-v3\_default.elf](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.elf) (**stable** build, **recommended**, for **debugging**)\

* [Download nxp\_fmuk66-v3\_default.px4](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.px4) (latest **development** build, for use with **QGroundControl**)
* [Download nxp\_fmuk66-v3.bin](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3.bin) (latest **development** build, for use with **J-Link Commander**)
* [Download nxp\_fmuk66-v3\_default.elf](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.elf) (latest **development** build, for **debugging**)

{% hint style="info" %}
In order to use PX4 Autopilot with the RDDRONE-FMUK66, you first need to [flash a bootloader using J-Link commander](userguide/programming.md#programming-the-bootloader). The **bootloader binary** must be present at memory address 0x0000. When you manually flash the PX4 firmware as well, keep in mind that the the **PX4 binary** has to be [written from memory address 0x6000 onwards](userguide/programming.md#programming-the-firmware). After the bootloader has been flashed you can also use QGroundControl to flash firmware to the board.
{% endhint %}

The RDDRONE-FMUK66 (NXPhlite) is fully supported by PX4 Autopilot. It is recommended to start with the latest stable version. An overview of releases is [available on GitHub](https://github.com/PX4/Firmware/releases).&#x20;

When updating PX4 firmware through **QGroundControl**, it is not necessary to download a firmware binary separately. QGroundControl can do this for you. It will upload the latest stable release to your FMU by default, but you can also select the latest development build or a custom binary (.px4 or .bin file).

The [latest stable release of PX4 for the RDDRONE-FMUK66](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/) is also available on the [PX4 CI server](http://ci.px4.io). Several files are available. The .px4 files (also available on GitHub) can be used with the custom binary option in QGroundControl. J-Link Commander requires a .bin file for writing the software to the board. The .elf can be used for debugging purposes.

The [latest development version (unstable)](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/) can also be directly downloaded from the CI server. Please keep in mind that these builds might be untested and could still include serious bugs.

Guides are available for [updating firmware](userguide/qgroundcontrol/firmware.md), and [building the firmware](developerguide/building-firmware.md) from source.

## RDDRONE-FMUK66 PX4 bootloader

(Note: NXP does not provide precompiled code. Binary courtesy of PX4.io)

* [Download fmuk66v3\_bl.bin](http://ci.px4.io/job/PX4/job/PX4-Bootloader/job/master/lastSuccessfulBuild/artifact/build/fmuk66v3\_bl/fmuk66v3\_bl.bin)

A precompiled PX4 bootloader is available for convenience. This file will be updated infrequently and usually without notice. There is usually no need to update the bootloader after it is loaded once.

{% hint style="info" %}
It is **recommended** to update the bootloader on your RDDRONE-FMUK66 if it was **build from master before December 2019** or if was **downloaded from this page before April 2020**.
{% endhint %}

This GitBook has a guide for [programming software using the J-Link debugger](developerguide/program-software-using-debugger.md). The bootloader binary has to be **programmed at memory address 0x0000** on the RDDRONE-FMUK66. There are also instructions for [building the bootloader ](developerguide/building-bootloader.md)from source, in case you ever need it.

## QGroundControl

* [Download QGroundControl](https://docs.qgroundcontrol.com/en/getting\_started/download\_and\_install.html) (**Stable** release, **recommended**)
* [Download QGroundControl](https://docs.qgroundcontrol.com/en/releases/daily\_builds.html) (Daily build / **development** release)

QGroundControl is the ground control software (GCS) of choice within the [Dronecode platform](https://www.dronecode.org/platform/). It can be used to configure and control any FMU that runs PX4 or a MAVLink compatible flight stack. It is recommended to use the latest stable release and update regularly when new releases become available.

## J-Link Software and Documentation Pack

* [Download J-Link Software and Documentation Pack](https://www.segger.com/downloads/jlink#J-LinkSoftwareAndDocumentationPack)

J-Link Commander is used to flash binaries onto the RDDRONE-FMUK66 board. The latest (stable) release of the J-Link Software and Documentation Pack is available at the SEGGER website for different operating systems.

## FlySky-i6S radio controller firmware updater

* [Download FlySky-i6S firmware updater](https://www.flysky-cn.com/fsi6s) (click the firmware button at the bottom of the page)

The firmware on the radio controller can be updated by connecting the transmitter to your PC with a micro-USB cable. Go to the settings menu on the controller, and select "Firmware update". Run the firmware updater tool on your PC to update the firmware on your controller.

## Virtual COM Port drivers for FTDI / USB-TTL-3V3 cable

* [Download Virtual COM Port Drivers](https://www.ftdichip.com/Drivers/VCP.htm)

In some cases you might need to install a VCP driver for the FTDI (USB-TTL-3V3) cable. It is available for Windows and Mac OS. For Windows there is a setup executable available in the "Comments" column.
