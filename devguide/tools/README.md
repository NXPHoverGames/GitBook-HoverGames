---
description: >-
  This section explains how to set up the basic development tools needed for the
  HoverGames.
---

# Development tools

This section explains setting up software for running a virtual machine, creating such a virtual machine, and installing the required development tools inside it.

{% hint style="success" %}
[A preconfigured virtual machine is available on our downloads page](../../downloads.md#preconfigured-virtual-machine-image-with-development-tools). It already includes the development tools with the recommend configuration. You still need to [download ](../../downloads.md#oracle-vm-virtualbox)and install VirtualBox. You can import the VM into VirtualBox by going to File -&gt; Import Appliance...

If you choose to download the preconfigured VM, you do not have to follow the instructions in the rest of this section. However, **it will be still be useful to read these pages**, as it will provide insight in how the tools are setup and how you can use them. Also, you might want to [enable some extra resources](virtual-machine.md#virtual-machine-properties) for your virtual machine if your computer is powerful enough.

Note that the default _hovergames_ useraccount also has _hovergames_  as its password!
{% endhint %}

We will start with [setting up the VirtualBox software](virtual-machine.md) for creating and running a virtual machine. We will also create the virtual machine, in which we will [install the Ubuntu Linux operating system](installing-ubuntu.md). Inside this virtual machine, the basic [PX4 toolchain will be installed](toolchain-installation.md), which should provide all the tools already to build your own firmware binaries from source.

Finally, you will have the choice to install and setup an integrated development environment \(IDE\), which allows you to edit, build and debug the PX4 firmware. The recommend IDE is [MCUXpresso](mcuxpresso.md), but we also provide instructions for setting up the popular [Visual Studio Code](visual-studio-code.md).

It is very well possible to install all tools on your main operating system, whether you are using Linux, Windows or MacOS. However, we only provide the instructions for setting up a virtual machine, because this should work well for most users and it is easier to support a single platform. You are free to install the tools onto your main operating system, but please be aware that you might need to figure some things out  using other resources. While these tools are cross platform, it should be noted that the majority of developers use Linux or MacOS. 

