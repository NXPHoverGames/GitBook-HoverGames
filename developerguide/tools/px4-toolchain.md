---
description: >-
  How to install the development toolchain for the PX4 firmware and other
  Dronecode and PX4 related software packages.
---

# PX4 Toolchain

To start building PX4 firmware from source, you should first install the PX4 toolchain. This provides you with all the tools required to develop PX4 firmware versions, but also build them in general. You could directly install the toolchain on your main operating system, but we recommend to install it inside the virtual machine we created as described on the previous pages.

## Download and run the convenience bash script

The PX4 developers provide convenience bash scripts for Ubuntu to easily setup the tools required to build the PX4 firmware. Before you get started, run the following commands \(inside your virtual machine\) to add your useraccount to the "dialout" group, and install screen, which will be useful later:

```bash
sudo usermod -a -G dialout $USER
sudo apt install screen
```

After you have run these commands, logout and login again, or simply reboot the virtual machine with the `sudo reboot` command.

Now, download the convenience bash script using the following command, or use your browser to download the file and save it to your home folder.

```bash
wget https://raw.githubusercontent.com/PX4/Devguide/master/build_scripts/ubuntu_sim_nuttx.sh
```

You can now start the script by running the following command in your terminal:

```bash
source ubuntu_sim_nuttx.sh
```

Now it's time to do a reboot. Either manually go to the menu and reboot the VM, or enter the `reboot` command in the terminal.

## Make your first PX4 build

The convenience bash script should have cloned the PX4 repository into your home folder, at the location `~/src/Firmware`. You can now make your first build using the command:

```bash
cd ~/src/Firmware && make nxp_fmuk66-v3_default
```

After the build process is done, you should be able to find `.bin`, `.px4` and `.elf` files in the `~/src/Firmware/build/nxp_fmuk66-v3_default` folder. We will later come back to building your own firmware binaries, when we set up an IDE \(integrated development environment\) to do it for us.

## Install QGroundControl inside the VM

It is also a good idea to install the latest daily build release of QGroundControl inside your VM. It generally works better with the latest features of PX4, that you might come across when you use the latest PX4 source code that might not have been released as a stable version yet. Also, it is easier to switch between different AppImages in Linux than it is to reinstall a different QGroundControl in Windows.

Links to the daily builds are provided in the QGroundControl documentation. Inside your VM you need the Linux version, which is provided as an AppImage:

{% embed url="https://docs.qgroundcontrol.com/en/releases/daily\_builds.html" %}

You don't need to install an AppImage. You only need to make it executable and run it. Move the AppImage file to your homefolder. Then, right click on the file, go to the file properties, and give the AppImage permission to execute as a program.

![](../../.gitbook/assets/image%20%28137%29.png)

Alternatively, you can make the file executable by running the command, assuming it is located in your home folder:

`chmod +x ~/QGroundControl.AppImage`

More information about using an AppImage is available in the QGroundControl User Guide:

{% embed url="https://docs.qgroundcontrol.com/en/getting\_started/download\_and\_install.html\#appimage" %}

You are now ready to continue to the next section\(s\), in which we will set up an integrated development environment \(IDE\) to edit, build and debug the PX4 firmware. You can choose to install either [MCUXpresso](mcuxpresso.md) \(recommended\) or [Visual Studio Code](mcuxpresso.md), but you can also install both to see which one you like best.

## Instructions from the PX4 Developer Guide

By following the steps provided above, you should be ready to build the PX4 firmware from source. In case you want more information, toolchain installation instructions are also available at the PX4 Developer Guide. **Note that you do not need to follow these instructions if you have already installed the toolchain according to the steps above.**

{% embed url="https://dev.px4.io/master/en/setup/dev\_env\_linux.html" %}

For Linux computers, you only need to install the `Pixhawk/NuttX (and jMAVSim)` version \(so follow the steps at [https://dev.px4.io/master/en/setup/dev\_env\_linux.html](https://dev.px4.io/master/en/setup/dev_env_linux.html) up to the `Snapdragon Flight` heading\).

For Windows computers, we recommend the Cygwin installation, which can be installed using the steps at [https://dev.px4.io/master/en/setup/dev\_env\_windows\_cygwin.html](https://dev.px4.io/master/en/setup/dev_env_windows_cygwin.html) up to the `Usage Instructions` heading. 

Another option for Windows users is to setup a Linux virtual machine and just install the Linux toolchain. That's exactly what we have done above, actually. The PX4 Developer Guide also provides a step-by-step guide for this: [https://dev.px4.io/master/en/setup/dev\_env\_windows\_vm.html](https://dev.px4.io/master/en/setup/dev_env_windows_vm.html)

Instructions for Mac OS are available as well, at [https://dev.px4.io/en/setup/dev\_env\_mac.html](https://dev.px4.io/master/en/setup/dev_env_mac.html).

