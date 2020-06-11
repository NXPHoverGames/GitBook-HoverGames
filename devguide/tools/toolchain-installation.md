---
description: >-
  How to install the development toolchain for PX4 Autopilot and other Dronecode
  software projects.
---

# Toolchain installation

To start building PX4 firmware from source, you should first install the PX4 toolchain. This provides you with all the tools required to develop, build and debug PX4 Autopilot, but the same tools are also often used for other software projects. You could directly install the toolchain on your main operating system, but we recommend to install it inside the virtual machine we created as described on the previous pages.

## Install Git

The minimal installation that we selected does not include Git by default. Git is a very popular distributed version-control system and you will probably use it a lot when developing software for the HoverGames.  It will also allow us to easily download \("clone"\) the PX4 code because it is available on GitHub, which is a Git-based source code hosting platform. 

So let's install Git using the following command:

```bash
sudo apt install git
```

![](../../.gitbook/assets/hg_vm42.png)

## Download the PX4 source code

Before we install any tools we will download the PX4 source code. The PX4 developers have included a script that makes it much easier to install all required tools. Let's first create a folder to hold all sourcecode that we are going to work with. The following command creates the "src" folder in the user's home folder \(if it doesn't exist already\) and then changes the working directory to this folder:

```bash
mkdir -p ~/src && cd ~/src
```

The next step is to actually download the source code. We will use Git to create a local copy of the online repository that is hosted on GitHub. The following command will "clone" the whole repository, including submodules, in a new "px4-firmware" folder.

```bash
git clone --recursive https://github.com/PX4/Firmware.git px4-firmware
```

Note that it will take a while to clone the whole repository. The PX4 source code should now be available in the `~/src/px4-firmware` folder. The tilde represents the current user's home folder within the file system. You can also browse to this location with the file manager.

![](../../.gitbook/assets/hg_vm43.png)

## Install the toolchain

As already mentioned, the PX4 developers provide a bash script to easily install all the tools that you need to build the PX4 firmware. We already cloned the PX4 source code, so we can just change our working directory and run the script:

```bash
cd ~/src/px4-firmware && bash ./Tools/setup/ubuntu.sh
```

You should reboot the virtual machine after the installation is done.

![](../../.gitbook/assets/hg_vm44.png)

![](../../.gitbook/assets/hg_vm45.png)

## Make your first PX4 build

Make sure to reboot your computer after the toolchain installation is finished. Then change your working directory to the PX4 firmware repository and start a build for the FMUK66 using the following command:

```bash
cd ~/src/px4-firmware && make nxp_fmuk66-v3_default
```

After the build process has finished, you should be able to find `.bin`, `.px4` and `.elf` files in the `~/src/px4-firmware/build/nxp_fmuk66-v3_default` folder. We will later come back to building your own firmware binaries, when we set up an IDE \(integrated development environment\) to do it for us.

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



