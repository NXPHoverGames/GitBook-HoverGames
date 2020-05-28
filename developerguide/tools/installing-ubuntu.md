---
description: This page explains how to install Ubuntu inside the virtual machine.
---

# Installing Ubuntu

## Installing Ubuntu to the virtual disk image

When you run your virtual machine for the first time, you will be greeted by a screen that asks you to try Ubuntu or directly install it. You can also select a different language, if you want. We will start with directly installing Ubuntu.

![](../../.gitbook/assets/image%20%28114%29.png)

### Keyboard layout

If desired, you can change the keyboard layout. Usually, the US layout works fine as well.

![](../../.gitbook/assets/image%20%2851%29.png)

### Updates and other software

Choose a **minimal installation**. It is useful to also **install updates** and **third party software** while installing Ubuntu.

![](../../.gitbook/assets/image%20%2874%29.png)

### Installation type

Choose to **erase the disk and install Ubuntu**. Don't worry, this will only "erase" your virtual hard disk image, not your actual hard drive. After pressing "**Install Now**", you might get a pop-up that asks if you want to write the changes to the disk, just press **continue**. After that, you might have to wait for a few minutes.

![](../../.gitbook/assets/image%20%2879%29.png)

### Where are you?

The next screen will ask for your location. The default will probably work fine, otherwise select the option that matches your current location the best.

![](../../.gitbook/assets/image%20%28122%29.png)

### Who are you?

After this, you will be asked to set up a user account. For this virtual machine, we just use a generic name and password to make it easy to use. Fill in "HoverGames" for the **user account name** and the **computer name**. For the **username** and **password**, use the lowercase "hovergames". You can also select the option to **log in automatically**.

![](../../.gitbook/assets/image%20%2854%29.png)

It will take a while to finish the installation. You might be asked to **restart** the virtual machine after the installation has finished, just restart it immediately using the button. During shutdown, Ubuntu might also ask to remove the installation medium. You can ignore this and **press the enter key**.

## First boot

When the system reboots, you will be greeted by a screen that shows what's new in this Ubuntu version. Just click "Next" at the top right until you are asked to **help improve Ubuntu**. You can **disable** it, if you want. Then just continue until you are done and see the desktop.

![](../../.gitbook/assets/image%20%281%29.png)

You might also get a popup from the software updater. It is recommended to **install these updates** now. You might be prompted to enter your password, which should be "hovergames" \(lowercase\). After the updates are installed you might be asked to **restart** again. Just restart before we continue.

![](../../.gitbook/assets/image%20%2878%29.png)

## VirtualBox Guest Additions

Next, we will install the Guest Additions. This will provide better integration between your guest OS and host OS. Open a terminal window by going to the menu \(the icon with the 9 dots at the bottom\) and search for the terminal application. Once you have it opened, don't forget to right click the icon in your launcher and add it to your favorites. You will be using the terminal often. You can probably remove the "Help" and "Ubuntu Software" icons from your launcher, you will probably not use them much. You can always find them through the menu.

![](../../.gitbook/assets/image%20%28133%29.png)

Now, install the Guest Additions through the package manager using the command in the terminal:

```bash
sudo apt install virtualbox-guest-dkms
```

You will probably be asked whether you want to install the packages or not. You should enter "y" \(for "yes"\) in the terminal and press enter. It may take a while to install.

The version of the Guest Additions provided through the default repositories is probably not for the latest version of VirtualBox, so it might give some issues. However, it is still useful to install it because it will automatically install useful dependency packages as well. To now easily upgrade to the latest version of the Guest Additions, go to the "Devices" menu and use the "Insert Guest Additions CD image".

![](../../.gitbook/assets/image%20%28103%29.png)

It will ask you whether you want to run the software, and may prompt you for your password. It will start a terminal window and may complain about some packages not being installed, but that should be no problem right now. Once the installation finishes, you can close the terminal window. After the installation is done, you should be able to maximize the virtual machine window, and the resolution of the Ubuntu desktop should scale with the screen size. Also, you should be able to use the shared clipboard. If it does not work yet, you might need to reboot the virtual machine again.

![](../../.gitbook/assets/image%20%2876%29.png)

## Shared folders

To make the shared folder work, we also need to add our useraccount to the vboxsf group. 

Inside the terminal, type the command `sudo usermod -aG vboxsf hovergames`, this will give you access to the shared folders. You might be prompted for your password. You possibly have to reboot before it becomes active. If after a reboot the shared folder is still not visible from the file manager inside the VM, you might need to check the virtual machine settings to see if the shared folder has automount enabled.

![](../../.gitbook/assets/image%20%2835%29.png)

## Some useful settings

Something that might still be useful to do at this point, is to make sure all language packages are installed. This is especially useful when you did not select English as the default language. Go to the menu and look for "Language Support". When you open it, it will immediately ask you to install the missing language packages.

![](../../.gitbook/assets/image%20%2898%29.png)

Finally, from the menu you can also find "Settings". Go to "Power" and set power saving to never. This is the last setting for now. Your basic virtual machine should be fully operational now and you can customize it the way you want. The next section will discuss setting up the actual development tools inside your virtual machine.

![](../../.gitbook/assets/image%20%28136%29.png)

