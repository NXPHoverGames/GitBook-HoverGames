---
description: >-
  We are going to set up a Linux virtual machine that can be used for
  developing, building and debugging software for HoverGames and other NXP
  Mobile Robotics platforms.
---

# Virtual machine

Most of the popular tools that you can use to develop software for the HoverGames drone kit are best supported under a Linux operating system. Therefore it is strongly recommended to either use a native Linux setup, or a virtual machine (VM) running Linux on top of a Windows (or Mac) operating system. Using a VM instead of a native setup comes at the cost of processing power and flexibility, but should not be a big issue if you have a modern computer.

## Ubuntu and VirtualBox

It is strongly recommended to use a recent Ubuntu LTS (long-term support) version as the basis of your development environment. It is a beginner-friendly Linux distribution that is widely used for software development. Most of our required tools are guaranteed to work on recent Ubuntu versions. As of August 2022, the PX4 Autopilot build system supports Ubuntu 18.04, Ubuntu 20.04 as well as Ubuntu 22.04. We **strongly recommend to use Ubuntu 20.04** because it is also supported by most NXP tools, though all instructions have also been tested with Ubuntu 22.04. Use of another Linux distribution or Ubuntu version may give some unexpected issues.

You can download the "desktop image" (.iso file) for free from the Ubuntu website:

{% embed url="https://releases.ubuntu.com/20.04/" %}

VirtualBox is a beginner-friendly and cost-effective package for creating and running virtual machines, because it is also an open source project and available free of charge. As of August 2022, the latest version is VirtualBox 6.1.36. Please install VirtualBox and all of its components on your computer before you continue. &#x20;

{% embed url="https://www.virtualbox.org/wiki/Downloads" %}

{% hint style="warning" %}
VirtualBox provides an "Extension Pack", which provides support for USB 2.0 and USB 3.0 devices. It is not strictly required, but may improve the performance of USB devices when used with a VM.

However, this Extension Pack is [licensed free for personal use only](https://www.virtualbox.org/wiki/Licensing\_FAQ), which should be okay for most HoverGames participants, but commercial users are asked to pay a fee:

"The VirtualBox Extension Pack is available under the [VirtualBox Extension Pack Personal Use and Evaluation License](https://www.virtualbox.org/wiki/VirtualBox\_PUEL), which is a free license for personal, educational or evaluation use, or an Enterprise License, which is a for-fee license that allows most commercial, non-distribution uses restricted by the PUEL."

Employees of NXP Semiconductors or other organizations should check with their IT departments for license requirements and costs.
{% endhint %}

## Creating the virtual machine

Open VirtualBox and create a new virtual machine using the **blue "New" button** at the top of the screen, or using the "New..." option under the "Machine" tab. Fill in a descriptive and easily recognizable **name** for your virtual machine, such as "NXP HoverGames" or "NXP Mobile Robotics". The default machine folder location should be okay, but may be changed if you want. The type should be changed to **Linux** and the right version is **Ubuntu (64-bit)**.

{% hint style="warning" %}
If your computer appears to **not support 64-bit** **guest operating systems**, you may need to enable hardware virtualization in your BIOS/UEFI. Look for settings that are called something like "Enable VT-x" (for Intel processors) or "Enable AMD-V" (for AMD processors).

* On corporate-managed Windows 10 machines it may also be that [credential guard is enabled](https://support.microsoft.com/en-us/help/3204980/virtualization-applications-do-not-work-together-with-hyper-v-device-g). You probably have to contact your IT department about this.
{% endhint %}

![](../../.gitbook/assets/createvirtualmachine.png)

Set the memory size to **at least 4096 MiB**, assuming you have at least 8 GiB of RAM available on your computer. It is recommended to allocate even more memory to your virtual machine if your computer has more RAM installed. For example, if your computer has 16 GiB RAM, you can usually allocate 8 GiB (8192 MiB) to the VM without issues. More allocated memory generally means a more responsive virtual machine and quicker software builds. Less than 4096 MiB might work, but your VM will probably be very slow.

![](../../.gitbook/assets/hg\_vm2.png)

The next window will ask you to add a virtual hard disk. Choose the option to create a new one. The default **VDI file format** is fine, and it is a good idea to make it **dynamically allocated**. You can keep the default name. Please increase the size of the virtual hard disk to at least **60.00 GB**. This will be the maximum amount of space that the virtual hard disk may (eventually) use.

![](../../.gitbook/assets/hg\_vm3.png)

![](../../.gitbook/assets/hg\_vm4.png)

![](../../.gitbook/assets/hg\_vm5.png)

![](../../.gitbook/assets/hg\_vm6.png)

## Virtual machine settings

Select your newly created virtual machine and click the **orange "Settings" button** at the top of the screen, or the "Settings..." option under the "Machine" tab.

Under "General", go to the "Advanced" tab. **Enable the shared clipboard and set it to bidirectional**. It allows you to easily copy and paste text between your host and guest operating systems. You may also enable the drag'n'drop feature, but this has not been the most stable feature of VirtualBox. It is easier to work with a shared folder, which we will create later.

![](../../.gitbook/assets/hg\_vm7.png)

Under "System", you can go to the "Processor" tab. Assuming your CPU has at least 4 cores, you should **add at least a second core** to your virtual machine. If your CPU has more cores you can even **consider to add a third and a fourth**. This will generally make your virtual machine more responsive and speeds up software builds tremendously.

![](../../.gitbook/assets/hg\_vm8.png)

Under "Display", you can **increase the video memory**. You usually want to set this to the maximum value available, but any value within the green range should work well. The green range is the recommended range based on your computer hardware and the selected guest OS.

![](../../.gitbook/assets/hg\_vm9.png)

Under "Storage", select the **empty disk drive in the middle of the window**, then click on the small disk icon on the right side of the window and look for the "Choose a disk file..." option. Then find the Ubuntu .iso file you downloaded before. The right file might also be listed in the menu already!

![](../../.gitbook/assets/hg\_vm10.png)

If you have the VirtualBox Extension Pack installed, you can select the USB 2.0 or USB 3.0 controller under "USB". Otherwise you will be stuck with the USB 1.1 controller, which should be fine as well. The USB 2.0 controller is the default option when the extension pack is installed, but you may opt to select the USB 3.0 controller if you want to use superspeed USB devices.

![](../../.gitbook/assets/hg\_vm11.png)

While you're at this screen, consider to **add some filters for the USB devices** that you will be using. This allows the virtual machine to access these devices whenever they are plugged into your computer while the VM is running. Note that these devices will then not be available on your host operating system. You can also add filters at a later time or pass through USB devices manually.

To easily add a device filter, make sure the device is plugged in and click on the icon with the "+" sign. It is recommended that you add filters for the FMUK66, the J-Link debugger and the USB-UART cable.

![](../../.gitbook/assets/hg\_vm12.png)

For just a few seconds after you plug in the FMU, the "NXP SEMICONDUCTORS PX4 BL FMUK66 E" device will be available in the list. This is the bootloader. After a few seconds, this device will disappear and "NXP SEMICONDUCTORS PX4 FMUK66 E" will appear. Note that this is only the case if the FMU [already has a bootloader and firmware installed](../../userguide/programming.md)!&#x20;

Make sure to add filters for both the FMUK66 bootloader and the "standard" FMUK66 device. If you don't see the bootloader device in the list, make sure the FMU is not powered by anything else than the USB cable. Plug the USB cable in again and quickly click the icon while the bootloader is still active (orange LED on the FMU will blink). You have to do this quickly!

Also, make sure to plug in the debugger and USB-TTL-3V3 cable and add filters for "SEGGER J-Link" and "FTDI TTL232R-3V3" (or a name that looks similar). Be aware that the telemetry radios may also present themselves as a FTDI USB UART device if you have one connected to your computer! Their product number should be slightly different, but it's better to disconnect them to avoid confusion.

The list should look similar to this:

![](../../.gitbook/assets/hg\_vm13.png)

Under "Shared Folders", we can also setup a folder that will be accessible on both your host and guest operating systems. Please **create an empty folder** on your host operating system. The folder name should be short and clear. This name will be used to identify the folder in the guest operating system (Ubuntu). You can also enable **auto-mount**. This will make sure that the shared folder is automatically mounted after the virtual machine has booted, but first we have to install the OS including guest additions.&#x20;

![](../../.gitbook/assets/hg\_vm14.png)

You can now **press the green "Start" button** to run your virtual machine. You may be asked first to select the right boot disk, make sure you select the Ubuntu image. The VM should then start and boot from the provided .iso disk image, starting the installation process for Ubuntu. We will continue on the next page and guide you through this process.

![](../../.gitbook/assets/hg\_vm15.png)
