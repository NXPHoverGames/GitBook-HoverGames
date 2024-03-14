---
description: >-
  This section explains how to set up a Linux-based development environment with
  useful tools to develop, build and debug software for HoverGames and NXP
  Mobile Robotics platforms.
---

# Development tools

It is required to setup a Linux-based\* development environment, preferably based on Ubuntu 20.04 (or 22.04). If you are not running a Linux OS already, you can consider to install Ubuntu natively besides your Windows setup (dual-boot), or on a separate laptop. Another convenient option would be to use virtualization to run Linux on your Windows computer. There are plenty of tools available, such as Oracle VM VirtualBox, VMware Workstation and even the built-in Windows Subsystems for Linux (WSL).

{% hint style="info" %}
\*A native macOS-based development environment might also work, but not all tools are available. We cannot guarantee support - but you might be able to get help from other developers in the HoverGames community that work with macOS.
{% endhint %}

{% hint style="warning" %}
NXP and Dronecode used to provide a **preconfigured virtual machine** image for VirtualBox. This image was based on Ubuntu 18.04 and contained the required tools to start developing and debugging software for HoverGames. We **no longer recommend** using this image as most preinstalled tools are now outdated and would require significant work to get into a working state again.

A **fresh setup based on Ubuntu 20.04** (or 22.04) **is now recommended**. No preconfigured image will be made available however, as it would again become outdated within months after its initial release. It is more beneficial to learn yourself how to setup and maintain a Linux-based development environment - and it is not difficult!
{% endhint %}

The next pages will provide step-by-step instructions on how to install **Ubuntu 20.04** (though all instructions should also apply to Ubuntu 22.04 as well) with a proper toolchain to develop, build and debug Apache NuttX and PX4 Autopilot for RDDRONE-FMUK66 (Kinetis K66 MCU) as well as other NXP Mobile Robotics platforms.

The first part of the instructions will also explain [setting up the VirtualBox software](virtual-machine.md) for creating and running a virtual machine. NXP does not specifically endorse VirtualBox, but it is a free open source tool and it is a convenient way to start using Ubuntu as a beginner. More advanced developers may install Ubuntu natively or use different virtualization tools (e.g. VMware, WSL2).

The next step will explain how to [install the Ubuntu Linux operating system](installing-ubuntu.md). We will also [download and install the PX4 toolchain](toolchain-installation.md), which should provide all the tools already to build your own PX4 firmware binaries from source. The same tools can also be used to build Apache NuttX, which is the Real-Time Operating System (RTOS) that is used by PX4, but can also be used stand-alone.

Finally, we will [install NXP MCUXpresso](mcuxpresso.md), an integrated development environment (IDE) which allows you to edit, build and debug software for many NXP microcontrollers and processors. The instructions will explain how you can setup a project to build and debug PX4 Autopilot.
