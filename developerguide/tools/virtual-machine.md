---
description: >-
  In this section we will set up a virtual machine that can be used for
  developing and building the PX4 firmware and creating software for companion
  computers.
---

# Virtual machine

Most of the tools that are generally used for writing, building and debugging software for HoverGames, are best supported under a Linux operating system. Therefore, it is strongly recommended to either use a native Linux setup, or a virtual machine \(VM\) running Linux on a Windows or MacOS computer. In case you are not able to use a native Ubuntu setup, a virtual machine setup will work just fine. This comes at the cost of speed and flexibility, but should not be a big issue for most developers. In this guide, we will set up a virtual machine, but most instructions would also apply to a native setup.

{% hint style="success" %}
[A preconfigured virtual machine is available on our downloads page](../../downloads.md#preconfigured-virtual-machine-image-with-development-tools). It already includes the development tools with the recommend configuration. You still need to [download ](../../downloads.md#oracle-vm-virtualbox)and install VirtualBox. You can import the VM into VirtualBox by going to File -&gt; Import Appliance...

If you choose to download the preconfigured VM, you do not have to follow the instructions in the rest of this section. However, it will be still be useful to read these pages, as it will provide insight in how the tools are setup and how you can use them. Also, you might want to [enable some extra resources](virtual-machine.md#virtual-machine-properties) for your virtual machine if your computer is powerful enough.

Note that the default _hovergames_ useraccount also has _hovergames_  as its password!
{% endhint %}

## Ubuntu and VirtualBox

The recommended Linux distro is the latest Ubuntu LTS \(long-term support\) version. As of June 2019, the latest LTS version is Ubuntu 18.04.2. It is available for free from the Ubuntu website. The download should be an .iso image file.

{% embed url="https://ubuntu.com/download/desktop" %}

The recommended package for creating and running virtual machines is VirtualBox, because it is also available free of charge. As of June 2019, the latest version is VirtualBox 6.0.8. 

### Virtual Box Extension Pack

A VirtualBox Extension Pack is also available, which is also a good idea to install because it provides better USB support. Please install VirtualBox and all of its components on your computer before you continue.  

"The VirtualBox Extension Pack is available under the [VirtualBox Extension Pack Personal Use and Evaluation License](https://www.virtualbox.org/wiki/VirtualBox_PUEL), which is a free license for personal, educational or evaluation use, or an Enterprise License, which is a for-fee license that allows most commercial, non-distribution uses restricted by the PUEL."

{% hint style="warning" %}
The VirtualBox Extension Pack is licensed free for personal use. NXP and other organizations should check with their IT departments for licence costs. [https://www.virtualbox.org/wiki/Licensing\_FAQ](https://www.virtualbox.org/wiki/Licensing_FAQ)
{% endhint %}

{% embed url="https://www.virtualbox.org/wiki/Downloads" %}

## Creating the virtual machine

Open VirtualBox and create a new virtual machine using the "New" button at the top of the screen, or using the "New..." option under the "Machine" tab. Fill in a name for your virtual machine which you can easily recognize, such as "HoverGames VM". You can leave the save location to its default location. The type should be changed to "Linux" and the right version is "Ubuntu \(64-bit\)".

{% hint style="warning" %}
If your computer appears to **not support 64-bit** **guest operating systems**, you may need to enable hardware virtualization in your BIOS/UEFI. Look for settings that are called something like "Enable VT-x" \(for Intel processors\) or "Enable AMD-V" \(for AMD processors\).

* On corporate managed Windows 10 Machines it may also be that [credential guard is enabled](https://kb.vmware.com/s/article/2146361). You will likely need to talk with your IT department about this.

Even if your computer is not able to run 64-bit guest operating systems, you can still use an earlier Ubuntu 16.04.6 LTS release. It is still available as a 32-bit version on the [alternative downloads page](https://www.ubuntu.com/download/alternative-downloads). Not all described settings might be completely the same, but it should be possible to get everything to work on a 32-bit OS.
{% endhint %}

![](../../.gitbook/assets/image%20%2830%29.png)

Set the memory size to **at least 2048 MB**. If you have more memory available, it is recommended to add more memory to your virtual machine. For example, if your computer has 16 GiB RAM, you can easily add up to 8 GiB \(8192 MiB\) to the VM. More memory generally means a more responsive virtual machine and quicker software builds.

![](../../.gitbook/assets/image%20%2826%29.png)

The next window will ask you to add a virtual hard disk. Choose the option to create a new one. The default **VDI file format** is fine, and it is a good idea to make it **dynamically allocated**. You can keep the default name. Please increase the size of the virtual hard disk to **30.00 GB**. If you really want you can add more space, but this should be enough for now.

![](../../.gitbook/assets/image%20%2868%29.png)

![](../../.gitbook/assets/image%20%28109%29.png)

![](../../.gitbook/assets/image%20%28119%29.png)

![](../../.gitbook/assets/image%20%2870%29.png)

## Virtual machine settings

Select your newly created virtual machine and click the "Settings" button on top of the screen, or the "Settings..." option under the "Machine" tab.

Under "General", go to the "Advanced" tab. Enable the shared clipboard and set it to bidirectional. It allows you to easily copy and paste text between your host and guest operating systems. You can also enable the drag'n'drop feature, but this is usually a bit buggy and it is easier to work with a shared folder.

![](../../.gitbook/assets/image%20%2847%29.png)

Under "System", you can go to the "Processor" tab. If you CPU has at least 4 cores, you can easily add another core to your virtual machine. This will generally make your virtual machine more responsive and speeds up software builds.

![](../../.gitbook/assets/image%20%28152%29.png)

Under the "Acceleration" tab, make sure the "Enable VT-x/AMD-V" option is enabled.

![](../../.gitbook/assets/image%20%28126%29.png)

Under "Display", you could increase the video memory. While testing, setting the value to the maximum available amount worked fine. Any value within the green range should work well, as this is the recommended range based on your computer hardware and the selected guest OS.

![](../../.gitbook/assets/image%20%2815%29.png)

Under "Storage", select the empty disk drive and use the small disk icon on the right side of the window to select the Ubuntu .iso file you downloaded before.

![](../../.gitbook/assets/image%20%287%29.png)

If you have the VirtualBox Extension Pack installed, you can select the USB 2.0 or USB 3.0 controller under "USB". Otherwise you will be stuck with the USB 1.1 controller, which should be fine as well. The USB 2.0 controller is the default option when the extansion pack is installed. You can leave it like that for now.

![](../../.gitbook/assets/image%20%288%29.png)

While you're at this screen, also add some filters for the USB devices that you will be using. This automatically allows the virtual machine to access these devices whenever they are plugged into your computer while the VM is running. To easily add a device filter, make sure the device is plugged in and click on the icon with the "+" sign.

![](../../.gitbook/assets/image%20%2810%29.png)

When you plug in the FMU through USB, first the "NXP SEMICONDUCTORS PX4 BL NXPhlite v3.x" will pop-up, this is the bootloader. After a few seconds, this device will disappear and "NXP SEMICONDUCTORS PX4 FMUK66 v3.x" will appear. Make sure to add both of them. If you don't see the bootloader, make sure the FMU is not powered by anything else than the USB cable, and replug the USB cable and quickly click the icon. Also, make sure to plug in the debugger and FTDI \(USB-TTL-3V3\) cable and add the "SEGGER J-Link" and "FTDI FT232R USB UART" \(or similar devices\). Note that the telemetry radios also present themselves as a FTDI USB UART device if connected to your laptop! Their product number should be slightly different, though. The list should look something like this:

![](../../.gitbook/assets/image%20%2850%29.png)

Under "Shared Folders", we can also setup a folder that's accessible on both your host and guest operating systems. Please create and select a suitable folder on your host operating system, and give it a clear name that will be used by the guest OS. You can enable auto-mount, which should work after we have completely installed the virtual machine including guest additions.

![](../../.gitbook/assets/image%20%28161%29.png)

You can now press the start button to run your virtual machine. The VM should start and boot from the provided .iso disk image, starting the install procedure for Ubuntu. The next page will guide you through the installing Ubuntu inside the VM we just created.

