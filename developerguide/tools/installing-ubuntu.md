---
description: >-
  The next few steps will guide you through the Ubuntu installer. It does not
  matter if you install Ubuntu natively or in a virtual machine, the install
  procedure remains (mostly) the same.
---

# Installing Ubuntu

## Installer options

When you boot your (virtual) machine for the first time you will be greeted by a screen that asks you to try Ubuntu first or directly install it. You can select a different language, if you want, though it is recommended to stick to English if you want to follow along with these instructions. Then press the **Install Ubuntu** button to start the install procedure.

![](../../.gitbook/assets/hg\_vm16.png)

### Keyboard layout

If desired, you can change the keyboard layout. Note that the standard US layout is also often used in other countries. You can test if the setting is correct by typing some (special) characters in the field at the bottom of the screen.

![](../../.gitbook/assets/hg\_vm17.png)

### Updates and other software

We recommend to do a **minimal installation**. This will only install a minimal amount of additional software. Especially for users of a virtual machine this will help to keep the amount of occupied disk space low. It is also useful to already **install updates** and **third-party drivers**, as you would need to do this anyway after Ubuntu has been installed.

![](../../.gitbook/assets/hg\_vm18.png)

### Installation type

If you are installing Ubuntu within a virtual machine you can safely choose to **erase the disk and install Ubuntu**, as this will only "erase" your virtual hard disk image and not your actual hard drive. For a native setup you should consider whether you want to erase your disk or shrink the existing partition(s) and put Ubuntu on a second partition. After pressing "**Install Now**", you might get a pop-up that asks you to confirm that you want to write the changes to the disk, just press **continue**. After that, you might have to wait for a few minutes.

{% hint style="warning" %}
If you are installing Ubuntu **natively** you should do your own research about different installation types. If you have Windows installed on the same computer it will probably be detected by the Ubuntu installer and propose a dual-boot setup. This allows you to choose at boot between Windows and Ubuntu. However, this is beyond the scope of this GitBook - and there should be plenty information available on the internet to help you.
{% endhint %}

![](../../.gitbook/assets/hg\_vm19.png)

![](../../.gitbook/assets/hg\_vm20.png)

### Where are you?

The next screen will ask for your location/timezone. It should already provide a default location, which will probably work fine. If it does not match your city our country at all you can select one yourself.

![](../../.gitbook/assets/hg\_vm21.png)

### Who are you?

Finally, you will be asked to set up a user account. You can pick a **name** with which you want to be addressed by the system, for this example we will use "NXP". For compatibility reasons we suggest to use a strictly lowercase **computer name**, for example "nxpdev". If you are using a virtual machine you can just choose a simple **username** and **password** to make it easy to use, such as "nxp". You can also select the option to **log in automatically** for convenience. However, if you are installing Ubuntu on native hardware you should use a proper username and password combination, to keep your system secured.

![](../../.gitbook/assets/hg\_vm22.png)

It will take a while to finish the installation. You might be asked to **restart** the (virtual) machine after the installation is finished, just restart it immediately using the button. During shutdown, Ubuntu might also ask to remove the installation medium. You can ignore this when installing inside a virtual machine and immediately **press enter on your keyboard**.

![](../../.gitbook/assets/hg\_vm23.png)

![](../../.gitbook/assets/hg\_vm24.png)

## First boot

When the system reboots, you will be greeted by a screen that asks you to connect to your online accounts. You can just **skip** this for now, as well as the next few tabs, until you are asked to **help improve Ubuntu**. You can choose to not **send system info**, if you don't want to. Then just continue until you are done and see the desktop.

![](../../.gitbook/assets/hg\_vm25.png)

![](../../.gitbook/assets/hg\_vm26.png)

You might also get a popup from the software updater. It is recommended to **install these updates now**. You will most likely be prompted to enter your password. After the updates are installed you get asked to **restart** again, which you should do before we continue.

![](<../../.gitbook/assets/hg\_vm27 (1).png>)

![](../../.gitbook/assets/hg\_vm28.png)

![](../../.gitbook/assets/hg\_vm29.png)

## Install (even more) update

After the reboot we will (again) check for and install updates. Open a terminal window by going to the launcher menu (the icon with the 9 dots at the bottom of the dock) and search for the terminal application. Once you have it opened, don't forget to right click the terminal icon on the dock and add it to your favorites - you will be using the terminal much more often! You can also right click and remove the "Help" and "Ubuntu Software" icons from the dock, because you will probably not use them much. You can always find them again in the launcher menu.

![](../../.gitbook/assets/hg\_vm30.png)

We should first update the package lists of the apt package manager with the following command:

```bash
sudo apt update
```

The term "sudo" stands for "superuser do" and runs the command that follows with superuser privileges (administrator). You will probably be asked to enter your password. The terminal does not show your password while you type it, so it might seem as if nothing is happening, but just enter your password and press enter.

![](../../.gitbook/assets/hg\_vm31.png)

After the package lists have been updated, you will probably find that there are some updated packages available. We can install these updates with another command:

```bash
sudo apt upgrade
```

It will show you a list of packages that are going to be installed (not necessarily the same as shown in the screenshot below) and asks if you want to continue. You can press enter to select the capitalized default option ("Y" for "yes"). Now it might take a while to finish.

![](../../.gitbook/assets/hg\_vm32.png)

![](../../.gitbook/assets/hg\_vm33.png)

## VirtualBox users: install Guest Additions

We will now install the "VirtualBox Guest Additions", which are some packages that will provide better integration between your guest OS and host OS. Open a terminal and enter the following command:

```bash
sudo apt install build-essential dkms linux-headers-$(uname -r)
```

You will probably be asked again whether you want to install the listed packages. You can just press enter to continue. It might take a while to install.

{% hint style="info" %}
Copying and pasting commands between your host and guest operating systems is not yet possible. You will need to enter a few more commands yourself until we have installed the guest additions. After that you should be able to just copy the commands directly from these pages.
{% endhint %}

![](../../.gitbook/assets/hg\_vm34.png)

![](../../.gitbook/assets/hg\_vm35.png)

Go to the "Devices" menu and click on "Insert Guest Additions CD image". It will ask you whether you want to run the software, and may ask you to enter your password. It will then open a terminal window and start the installation.

![](../../.gitbook/assets/hg\_vm36.png)

![](../../.gitbook/assets/hg\_vm37.png)

Wait until the installation has finished and close the terminal window. You can then eject the guest additions disk image by right clicking on the icon on the desktop and selecting the eject option. Now that the guest additions are installed you should be able to maximize the virtual machine window, and the resolution of the Ubuntu desktop should scale with the window size. The shared clipboard should work as well. You might have to reboot the virtual machine again if it is not working.

{% hint style="info" %}
You should redo the last step **when you update VirtualBox**. You can just go to the device menu, insert the guest additions image and run the installer again. This will install the new version.
{% endhint %}

![](../../.gitbook/assets/hg\_vm38.png)

## VirtualBox users: setup shared folder

We [created a shared folder](virtual-machine.md#virtual-machine-settings) when we configured the virtual machine. To make it work within the VM we also need to add our user account to the vboxsf group. Enter the following command in a terminal window:

```bash
sudo usermod -aG vboxsf $USER
```

This will give you access to the shared folders. You might get asked for your password. You possibly have to reboot before it becomes active. If after a reboot the shared folder is still not visible from the file manager, you should check the virtual machine settings if the shared folder has auto-mount enabled.

![](../../.gitbook/assets/hg\_vm39.png)
