---
description: >-
  The PX4 project provides a set of recommended tools that you can use to
  develop, build and debug PX4 Autopilot and other Dronecode software projects,
  as well as Apache NuttX RTOS.
---

# PX4 toolchain

To start building PX4 Autopilot from source, you should first install the PX4 toolchain. This provides you with all the tools required to develop, build and debug PX4 Autopilot, but the same tools may also be used for other software projects, such as Apache NuttX.&#x20;

These tools can be installed for various operating systems, but are best supported for Ubuntu. Some tools or features may not work if installed on different operating systems. Therefore we recommended to install Ubuntu either natively or inside a virtual machine. The step-by-step instructions below will be specific to Ubuntu 20.04 (or 22.04) and may not work if you are using a different OS.

## Install Git

The minimal installation that we selected does not include Git by default. Git is a very popular distributed version-control system and you will probably use it a lot when developing software for the HoverGames.  It will also allow us to easily download ("clone") the PX4 code because it is available on GitHub, which is a Git-based source code hosting platform.&#x20;

So let's install Git using the following command:

```bash
sudo apt install git
```

![](../../.gitbook/assets/hg\_vm42.png)

## Download the PX4 source code

Before we install any tools we will download the PX4 Autopilot source code. The PX4 developers have included a script with their source code that makes it much easier to install all required tools. Let's first create a folder to hold all sourcecode that we are going to work with. The following command creates the "src" folder in the user's home folder (if it doesn't exist already):

```bash
mkdir -p ~/src
```

The next step is to actually download the source code. We will use Git to create a local copy of the online repository that is hosted on GitHub. The following command first changes the working directory to the "src" folder that we just created, then it will "clone" the whole PX4 Autopilot repository, including submodules, in a new "PX4-Autopilot" folder.

```bash
cd ~/src && git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

Note that it will take a while to clone the whole repository. The PX4 source code should now be available in the `~/src/PX4-Autopilot` folder. The tilde represents the current user's home folder within the file system. You can also browse to this location with the file manager.

![](../../.gitbook/assets/hg\_vm43.png)

## Install the toolchain

As already mentioned, the PX4 developers provide a bash script to easily install all the tools that you need to build the PX4 firmware. We already cloned the PX4 source code, so we can just change our working directory and run the script:

```bash
cd ~/src/PX4-Autopilot && bash ./Tools/setup/ubuntu.sh
```

You should reboot the (virtual) machine after the installation is done.

![](../../.gitbook/assets/hg\_vm45.png)

## Make your first PX4 build

Make sure to reboot your computer after the toolchain installation is finished. Then change your working directory to the PX4 Autopilot repository again and start a build for the FMUK66E using the following command:

<pre class="language-bash"><code class="lang-bash"><strong>cd ~/src/PX4-Autopilot &#x26;&#x26; make nxp_fmuk66-e_default
</strong></code></pre>

If you still have the older FMUK66 Rev. C or Rev. D then you should use a slightly different target:

```bash
cd ~/src/PX4-Autopilot && make nxp_fmuk66-v3_default
```

After the build process has finished, you should be able to find `.bin`, `.px4` and `.elf` files in the `~/src/px4-firmware/build/nxp_fmuk66-e_default` or `~/src/px4-firmware/build/nxp_fmuk66-v3_default` folder (depending on which target you have chosen). We will revisit the build process when we [set up the NXP MCUXpresso](mcuxpresso.md) integrated development environment (IDE) to edit, build and debug the PX4 firmware.

