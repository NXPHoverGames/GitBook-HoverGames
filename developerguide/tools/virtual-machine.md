---
description: >-
  We are going to set up a virtual machine running Ubuntu Linux that can be used
  for developing and building the PX4 firmware and creating software for
  companion computers.
---

# Virtual machine

Most of the tools that are generally used for writing, building and debugging software for the HoverGames are best supported under a Linux operating system. Therefore, it is strongly recommended to either use a native Linux setup, or a virtual machine \(VM\) running Linux on a Windows computer. In case you are not able to use a native Ubuntu setup, a virtual machine setup will work just fine. This comes at the cost of speed and flexibility, but should not be a big issue if you have a modern computer.

{% hint style="success" %}
[A preconfigured virtual machine is available on our downloads page](../../downloads.md#preconfigured-virtual-machine-image-with-development-tools). It already includes the development tools with the recommend configuration. You still need to [download ](../../downloads.md#oracle-vm-virtualbox)and install VirtualBox. You can import the VM into VirtualBox by going to File -&gt; Import Appliance...

If you choose to download the preconfigured VM, you do not have to follow the instructions in the rest of this section. However, it will be still be useful to read these pages, as it will provide insight in how the tools are setup and how you can use them. Also, you might want to [enable some extra resources](virtual-machine.md#virtual-machine-properties) for your virtual machine if your computer is powerful enough.

Note that the default _hovergames_ useraccount also has _hovergames_  as its password!
{% endhint %}

## Ubuntu and VirtualBox

It is strongly recommended to use a recent Ubuntu LTS \(long-term support\) version for developing your software. At the time of writing \(June 2020\), PX4 supports both Ubuntu 18.04 and Ubuntu 20.04, but we recommend to only use the Ubuntu 18.04 release because it is also supported by most NXP tools. You can download an an .iso image file for free from the Ubuntu website:

{% embed url="https://releases.ubuntu.com/" %}

The recommended package for creating and running virtual machines is VirtualBox, because it is also an open source project and available free of charge. As of June 2020, the latest version is VirtualBox 6.1.8. Please install VirtualBox and all of its components on your computer before you continue.  

{% embed url="https://www.virtualbox.org/wiki/Downloads" %}

{% hint style="warning" %}
A VirtualBox Extension Pack is also available, which is also a good idea to install because it provides support for USB 2.0 and USB 3.0 devices. It is not really needed, but it might be useful. Keep also in mind that this Extension Pack is [licensed free for personal use only](https://www.virtualbox.org/wiki/Licensing_FAQ), you have to pay a fee for commercial use.

"The VirtualBox Extension Pack is available under the [VirtualBox Extension Pack Personal Use and Evaluation License](https://www.virtualbox.org/wiki/VirtualBox_PUEL), which is a free license for personal, educational or evaluation use, or an Enterprise License, which is a for-fee license that allows most commercial, non-distribution uses restricted by the PUEL."

Employees of NXP Semiconductors or other organizations should check with their IT departments for licence costs.
{% endhint %}

## Creating the virtual machine

Open VirtualBox and create a new virtual machine using the blue "New" button at the top of the screen, or using the "New..." option under the "Machine" tab. Fill in a name for your virtual machine which you can easily recognize, such as "HoverGames". You can usually leave the save location to the default setting. The type should be changed to "Linux" and the right version is "Ubuntu \(64-bit\)".

{% hint style="warning" %}
If your computer appears to **not support 64-bit** **guest operating systems**, you may need to enable hardware virtualization in your BIOS/UEFI. Look for settings that are called something like "Enable VT-x" \(for Intel processors\) or "Enable AMD-V" \(for AMD processors\).

* On corporate managed Windows 10 Machines it may also be that [credential guard is enabled](https://kb.vmware.com/s/article/2146361). You probably have to contact your IT department about this.

Even if your computer is not able to run 64-bit guest operating systems, you can still use the older Ubuntu 16.04.6 LTS release. It is still available as a 32-bit version on its [release page](https://releases.ubuntu.com/xenial/). Not all steps and settings described here will be the same, but it should be possible to get everything to work on a 32-bit OS.
{% endhint %}

![](../../.gitbook/assets/hg_vm1.png)

Set the memory size to **at least 4096 MiB**, assuming you have at least 8 GiB of RAM available on your computer. It is recommended to add even more memory to your virtual machine if your computer has more RAM installed. For example, if your computer has 16 GiB RAM, you can easily add up to 8 GiB \(8192 MiB\) to the VM. More memory generally means a more responsive virtual machine and quicker software builds. Less than 4096 MiB might work, but your VM will probably be very slow.

![](../../.gitbook/assets/hg_vm2.png)

The next window will ask you to add a virtual hard disk. Choose the option to create a new one. The default **VDI file format** is fine, and it is a good idea to make it **dynamically allocated**. You can keep the default name. Please increase the size of the virtual hard disk to **50.00 GB**. This will be the maximum amount of space that the virtual hard disk will use. Under normal circumstances it will most likely stay below 20 GB. If you really want you can add more space, but this should be enough for now.

![](../../.gitbook/assets/hg_vm3.png)

![](../../.gitbook/assets/hg_vm4.png)

![](../../.gitbook/assets/hg_vm5.png)

![](../../.gitbook/assets/hg_vm6.png)

## Virtual machine settings

Select your newly created virtual machine and click the orange "Settings" button at the top of the screen, or the "Settings..." option under the "Machine" tab.

Under "General", go to the "Advanced" tab. Enable the shared clipboard and set it to bidirectional. It allows you to easily copy and paste text between your host and guest operating systems. You can also enable the drag'n'drop feature, but this is usually a bit buggy and it is easier to work with a shared folder.

![](../../.gitbook/assets/hg_vm7.png)

Under "System", you can go to the "Processor" tab. If you CPU has at least 4 cores, you can add a second core to your virtual machine. If your CPU has more cores you can even consider to add a third. This will generally make your virtual machine more responsive and speeds up software builds.

![](../../.gitbook/assets/hg_vm8.png)

Under "Display", you can increase the video memory. While testing, setting the value to the maximum available amount worked fine. Any value within the green range should work well, as this is the recommended range based on your computer hardware and the selected guest OS.

![](../../.gitbook/assets/hg_vm9.png)

Under "Storage", select the empty disk drive in the middle of the window, then click on the small disk icon on the right side of the window and look for the "choose a disk file..." option. Then find the Ubuntu .iso file you downloaded before.

![](../../.gitbook/assets/hg_vm10.png)

If you have the VirtualBox Extension Pack installed, you can select the USB 2.0 or USB 3.0 controller under "USB". Otherwise you will be stuck with the USB 1.1 controller, which should be fine as well. The USB 2.0 controller is the default option when the extansion pack is installed. You can leave it like that for now.

![](../../.gitbook/assets/hg_vm11.png)

While you're at this screen, also add some filters for the USB devices that you will be using. This automatically allows the virtual machine to access these devices whenever they are plugged into your computer while the VM is running. To easily add a device filter, make sure the device is plugged in and click on the icon with the "+" sign.

![](../../.gitbook/assets/hg_vm12.png)

When you plug in the FMU through USB, first the "NXP SEMICONDUCTORS PX4 BL FMUK66 v3.x" will be available in the list, this is the bootloader. After a few seconds, this device will disappear and "NXP SEMICONDUCTORS PX4 FMUK66 v3.x" will appear. Make sure to add both of them. If you don't see the bootloader, make sure the FMU is not powered by anything else than the USB cable. Plug the USB cable in again and quickly click the icon while the bootloader is still active \(orange LED on the FMU will blink\). 

Also, make sure to plug in the debugger and USB-TTL-3V3 cable and add filters for "SEGGER J-Link" and "FTDI FT232R USB UART" \(or a name that looks similar\). Note that the telemetry radios also present themselves as a FTDI USB UART device if connected to your laptop! Their product number should be slightly different, though. The list should look something like this:

![](../../.gitbook/assets/hg_vm13.png)

Under "Shared Folders", we can also setup a folder that's accessible on both your host and guest operating systems. Please create and select a suitable folder on your host operating system, and give it a clear name that will be used by the guest OS. You can enable auto-mount, which should work after we have completely installed the virtual machine including guest additions.

![](../../.gitbook/assets/hg_vm14.png)

You can now press the start button to run your virtual machine. The VM should start and boot from the provided .iso disk image, starting the install procedure for Ubuntu. The next page will guide you through the Ubuntu installation process.

