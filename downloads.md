---
description: An overview of useful software packages.
---

# Downloads

## QGroundControl

* [Download QGroundControl from QGroundControl.com](https://docs.qgroundcontrol.com/master/en/getting\_started/download\_and\_install.html) (**Stable** release, **recommended**)
* [Download QGroundControl from QGroundControl.com](https://docs.qgroundcontrol.com/master/en/releases/daily\_builds.html) (Daily build / **development** release)

QGroundControl is the ground control software (GCS) of choice within the [Dronecode platform](https://www.dronecode.org/platform/). It can be used to flash, configure and control any FMU that runs PX4 or a MAVLink compatible flight stack. It is recommended to use the latest stable release and update regularly when new releases become available.

## PX4 Autopilot builds for RDDRONE-FMUK66(E)

(Note: NXP does not provide precompiled code. Binaries are available through the courtesy of PX4)

Check below which file(s) you should download.

* [Download nxp\_fmuk66-v3\_default.px4](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.px4) (**stable** build for **Rev. C/D**, use with **QGC**)
* [Download nxp\_fmuk66-e\_default.px4](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-e\_default/nxp\_fmuk66-e\_default.px4) (**stable**, build for **Rev. E**, use with **QGC**)
* [Download nxp\_fmuk66-v3\_default.bin](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3.bin) (**stable** build for **Rev. C/D**, use with **J-Link**)
* [Download nxp\_fmuk66-e\_default.bin](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-e\_default/nxp\_fmuk66-e\_default.bin) (**stable** build for **Rev. E**, use with **J-Link**)
* [Download nxp\_fmuk66-v3\_default.elf](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.elf) (**stable** build for **Rev. C/D**, use for **debugging**)
* [Download nxp\_fmuk66-e\_default.elf](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/stable/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-e\_default/nxp\_fmuk66-e\_default.elf) (**stable** build for **Rev. E**, use for **debugging**)\

* [Download nxp\_fmuk66-v3\_default.px4](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.px4) (latest **dev.** build for **Rev. C/D**, use with **QGC**)
* [Download nxp\_fmuk66-e\_default.px4](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.px4) (latest **dev.** build for **Rev. E**, use with **QGC**)
* [Download nxp\_fmuk66-v3\_default.bin](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3.bin) (latest **dev.** build for **Rev. C/D**, use with **J-Link**)
* [Download nxp\_fmuk66-e\_default.bin](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3.bin) (latest **dev.** build for **Rev. E**, use with **J-Link**)
* [Download nxp\_fmuk66-v3\_default.elf](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.elf) (latest **dev.** build for **Rev. C/D**, use for **debugging**)
* [Download nxp\_fmuk66-e\_default.elf](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/nxp\_fmuk66-v3\_default.elf) (latest **dev.** build for **Rev. E**, use for **debugging**)

### Which variant and file type should I choose?

First you should determine whether to use the -v3 (Rev. C/D) or -e (Rev. E) build. This depends on when you got your RDDRONE-FMUK66. Rev. C and D boards have been distributed before 2022, but are still supported. New boards distributed since the beginning of 2022 are **most likely Rev. E**. You can also recognize a Rev. E board by the 8x RC PWM outputs (older boards had 6x PWM), or the small 2-pin NFC antenna connector on the side (which was not present on previous revisions).

Next you should consider whether you want to use the stable or development build. For flying it is generally **recommended to start with a stable build**. Only use a development build if you want to use experimental features or if you ran into a bug with the stable build. Note that it is very much possible that the development build introduces additional bugs - so be careful!

Finally you look at the purpose for which you need the binary. Are you flashing the FMUK66 board with a debugger (for example because you are using the board for the very first time), then you need the **.bin** file. If you have already flashed the board before and a bootloader has already been installed, then you can also upload it as a custom firmware binary through QGroundControl. For this you need the **.px4** file. Then there is also the **.elf** format which can be used with debugging software (e.g. GDB).

### Flashing PX4 Autopilot

{% hint style="info" %}
In order to use PX4 Autopilot with the RDDRONE-FMUK66, you first need to [flash a bootloader using J-Link commander](userguide/programming.md#programming-the-bootloader). The **bootloader binary** must be present at memory address 0x0000. When you manually flash the PX4 firmware as well, keep in mind that the the **PX4 binary** has to be [written from memory address 0x6000 onwards](userguide/programming.md#programming-the-firmware). After the bootloader has been flashed you can also use QGroundControl to flash firmware to the board.
{% endhint %}

After the bootloader has been installed, the PX4 firmware can be installed or updated through **QGroundControl.** When using QGC, it is not necessary to download a firmware binary separately. It will download and flash the latest stable release to your FMU by default, but you can also select the latest development build or a custom binary (.px4 or .bin file).

Guides are available for [updating firmware](userguide/qgroundcontrol/firmware.md), and [building the firmware](developerguide/building-firmware.md) from source.

## RDDRONE-FMUK66(E) PX4 bootloader

(Note: NXP does not provide precompiled code. Binaries are available through the courtesy of PX4)

* [Download nxp\_fmuk66-v3\_bootloader.bin](https://github.com/PX4/PX4-Autopilot/raw/main/boards/nxp/fmuk66-v3/extras/nxp\_fmuk66-v3\_bootloader.bin) (for **Rev. C/D**)
* [Download nxp\_fmuk66-e\_bootloader.bin](https://github.com/PX4/PX4-Autopilot/blob/main/boards/nxp/fmuk66-e/extras/nxp\_fmuk66-e\_bootloader.bin) (for **Rev. E**)

A precompiled PX4 bootloader is available for convenience. This file will be updated infrequently and usually without notice. There is usually no immediate need to flash newer bootloader versions.

{% hint style="info" %}
However, if you are ever having issues with flashing or booting newer versions of PX4 Autopilot, then that might be an indication that the bootloader needs to be updated.
{% endhint %}

This GitBook has a guide for [programming software using the J-Link debugger](developerguide/program-software-using-debugger.md). The bootloader binary has to be **programmed at memory address 0x0000** on the RDDRONE-FMUK66. There are also instructions for [building the bootloader from source](developerguide/building-bootloader.md), in case you ever need it.

## Oracle VM VirtualBox

* [Download Oracle VM VirtualBox from VirtualBox.org](https://www.virtualbox.org/wiki/Downloads)

It is required to setup a Linux-based\* development environment, preferably based on Ubuntu 20.04 (or 22.04). If you are not running a Linux OS already, you can consider to install Ubuntu natively besides your Windows setup (dual-boot), or on a separate laptop. However the **easiest option** might be to run it **virtually** from within your Windows OS. NXP does not endorse any specific tool. An often used option is [Oracle VM VirtualBox](https://www.virtualbox.org/), which is an open-source virtual machine hypervisor that can be used for free.

Our [Developer Guide](developerguide/tools/) contains further information and instructions on how to setup your own Linux-based development environment from scratch in e.g. VirtualBox.

{% hint style="info" %}
\*A native macOS-based development environment might also work, but not all tools are available. We cannot guarantee support - but you might be able to get help from other developers in the HoverGames community that work with macOS.
{% endhint %}

{% hint style="warning" %}
NXP and Dronecode used to provide a **preconfigured virtual machine** image for VirtualBox. This image was based on Ubuntu 18.04 and contained the required tools to start developing and debugging software for HoverGames. We **no longer recommend** using this image as most preinstalled tools are now outdated and would require significant work to get into a working state again.

A **fresh setup based on Ubuntu 20.04** (or 22.04) **is now recommended**. No preconfigured image will be made available however, as it would again become outdated within months after its initial release. It is more beneficial to learn yourself how to setup and maintain a Linux-based development environment - and it is not difficult!

**More information and instructions** are available in our [Developer Guide](developerguide/tools/)
{% endhint %}

{% hint style="warning" %}
There is an Extension Pack available for VirtualBox which includes support for USB 2.0 and USB 3.0 devices. It is not strictly required, but it improves performance of USB devices (e.g. the J-Link debugger) and you should therefore consider to also install the Extension Pack.

While the basic VirtualBox software is available free of charge for all users, the VirtualBox Extension Pack is only licensed free for **personal use**. [Commercial users have to pay for a license](https://www.virtualbox.org/wiki/Licensing\_FAQ). Employees of NXP Semiconductors or other organizations should check with their IT departments for license costs.
{% endhint %}

## J-Link Software and Documentation Pack

* [Download J-Link Software and Documentation Pack from SEGGER.com](https://www.segger.com/downloads/jlink#J-LinkSoftwareAndDocumentationPack)

J-Link Commander is used to flash binaries onto the RDDRONE-FMUK66 board. The latest (stable) release of the J-Link Software and Documentation Pack is available at the SEGGER website for different operating systems.

## FlySky-i6S radio controller firmware updater

* [Download FlySky-i6S firmware updater](https://www.flysky-cn.com/fsi6s) (click the firmware button at the bottom of the page)

The firmware on the radio controller can be updated by connecting the transmitter to your PC with a micro-USB cable. Go to the settings menu on the controller, and select "Firmware update". Run the firmware updater tool on your PC to update the firmware on your controller.

## Virtual COM Port drivers for FTDI / USB-TTL-3V3 cable

* [Download Virtual COM Port Drivers](https://www.ftdichip.com/Drivers/VCP.htm)

In some cases you might need to install a VCP driver for the FTDI (USB-TTL-3V3) cable. It is available for Windows and Mac OS. For Windows there is a setup executable available in the "Comments" column.
