---
description: >-
  The MCUXpresso Integrated Development Environment allows developers to edit,
  compile and debug code for many NXP microcontrollers. For HoverGames it is a
  useful tool for debugging the PX4 code.
---

# MCUXpresso

## Installing MCUXpresso

We will install MCUXpresso inside the Linux environment (native or virtual). This allows MCUXpresso to build PX4 Autopilot, flash it to the FMUK66E and debug the code while it is running on the board. You can also install MCUXpresso on your host operating system, but we recommend to keep all tools in the same (Linux) environment.

The MCUXpresso IDE is available free of charge and can be downloaded from the NXP website, but you will need to create a (free) NXP account:

{% embed url="https://www.nxp.com/design/software/development-software/mcuxpresso-software-and-tools-/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE" %}

Click on the download button and login to your NXP account. The next page will show the current available releases. There is also a tab for previous releases. You should download the current release (11.6 as of August 2022), click on "MCUXpresso IDE" to continue. You will have to agree with some terms and conditions before you can download the software.

Download the `.deb.bin` file for Linux. You can directly download it using the Firefox browser which is included with Ubuntu, or if you are using a virtual machine you can download it on your host operating system and move it into the [shared folder](installing-ubuntu.md#virtualbox-users-setup-shared-folder), which should be accessible in the file browser.

![](../../.gitbook/assets/hg\_mcuxpresso1.png)

Assuming you have the file stored in the `~/Downloads` folder, you should first enter the command below to allow the package to be executed and installed. You should replace the last part of the filename with the right version number for your download! You can use the auto-complete feature for this by pressing the tab key. Just start typing the command below and press tab when you get to the version number in the file name.

```bash
chmod +x ~/Downloads/mcuxpressoide-11.6.0_8187.x86_64.deb.bin
```

Now you can install MCUXpresso by executing the installer package, for which you again have to modify the filename to match the right version:

```bash
sudo ~/Downloads/mcuxpressoide-11.6.0_8187.x86_64.deb.bin
```

You might get asked to accept an agreement (use the arrow keys to select "Yes" and press enter). Then wait for the installation to finish.

![](../../.gitbook/assets/hg\_mcuxpresso2.png)

## Installing the Kinetis K66 SDK

Now we should start MCUXpresso. You can find it in Ubuntu's **launcher menu** (the icon in the bottom left corner of the screen). Look for the blue icon with the "X", or just type "MCUXpresso". MCUXpresso will immediately ask at what location the **workspace** should be saved. You can chose your own directory, or leave the default as is. You can also create additional workspaces for different projects if you want.

You will then be greeted by a welcome screen. You can **close the "Welcome" tab** or **press the "IDE" button on the top right** to continue. Once you are in the main view of the IDE, find the location were you stored the Kinetis K66 SDK .zip file, and **drag the archive** into the area of the IDE window that says "Installed SDKs". It's usually located at the bottom. It will ask you to confirm that you want to import the SDK. Just press "OK". It might take a few seconds to install.

![](../../.gitbook/assets/hg\_mcuxpresso5.png)

![](<../../.gitbook/assets/hg\_mcuxpresso6 (1).png>)

## Create a new project for PX4

Now that MCUXpresso and the Kinetis K66 SDK are installed, we can continue and create a PX4 project. You can create a new project in MCUXpresso by going to **"File", "New", and then "Project"**. A list with different project types will appear, from which you should select **"Makefile Project with Existing Code"** under "C/C++".

![](../../.gitbook/assets/hg\_mcuxpresso7.png)

You can use any project name, but for clarity we will call it "HoverGames PX4". You should select `/home/hovergames/src/px4-firmware` as the **existing code location**. This is the folder where we cloned the PX4 firmware code. Make sure that both the C and C++ languages are selected. For "Toolchain for Indexer Settings", select **"NXP MCU Tools"**. Click "Finish" to create the project.

![](../../.gitbook/assets/hg\_mcuxpresso8.png)

## Project properties

Before we continue we should change some project properties. **Select the project** we just created on the left side of the screen, go to **"Project"** in the menu at the top and then select **"Properties"**.&#x20;

Go to **"MCU Settings"** under "C/C++ Build". An error _might_ pop up, complaining about invalid values. If this happens you can close the error, switch to another tab and switch back again. You should now see the same screen as shown in the image below. On this "MCU Settings" screen, select the **MK66FN2M0xxx18** under the K6x family of MCUs.

![](../../.gitbook/assets/hg\_mcuxpresso9.png)

Now go to the main "C/C++ Build" tab. Uncheck "Use default build command" and change the build command to just `make`. The PX4 build scripts will take care of the specifics, we should not supply any additional arguments here.

![](../../.gitbook/assets/hg\_mcuxpresso10.png)

Then switch to the "Behavior" tab. Uncheck "Enable parallel build", because the PX4 build tools also already takes care of this. Set the "Build (incremental build)" target to `nxp_fmuk66-v3_default` and change the "Clean" target to `distclean`. Click "Apply" to apply all changed settings.

![](../../.gitbook/assets/hg\_mcuxpresso11.png)

You can click "Apply" to apply the changes, but don't close the window yet. The current configuration is named "Debug". Let's give that a more descriptive name. Click on the "Manage Configurations..." button and then choose "Rename..." to change the name. We will call it "PX4 FMUK66 Default". You can later add additional configurations if you want to play around with the build variables or if you want to build PX4 for another board, such as the [NXP UCANS32K146](https://nxp.gitbook.io/ucans32k146/).

![](../../.gitbook/assets/hg\_mcuxpresso12.png)

You can press "Apply and Close" to apply the changes and close the window.

We now have a _build_ configuration that allows us to create PX4 firmware builds for the FMUK66 board. You can use the hammer icon to start a build for the selected project. If you add multiple configurations you can switch between the different profiles with the small arrow next to the hammer icon.&#x20;

Give it a try, the console at the bottom of the IDE window will show the progress of the build. Note that this might take a while if you are building PX4 for the first time! When you make changes to the code after the first build it should only rebuild the changed files.

![](../../.gitbook/assets/hg\_mcuxpresso13.png)

## Run configuration

We can now build the PX4 firmware with MCUXpresso. We are now going to also add a _run_ configuration to flash the binary directly to the FMUK66 board with **just a USB cable**, without debugger!

{% hint style="info" %}
Flashing the PX4 firmware without a debugger is only possible [if the bootloader has already been flashed](../../userguide/programming.md) (with a compatible debugger and a tool such as JLink Commander).
{% endhint %}

At the top of the screen, you have a green "Run" icon. Click on the small arrow next to it, and select "Run Configurations...". In the window that opens, select "C/C++ Application" and click the "New" button above it. Name the newly created configuration "PX4 FMUK66 Upload (USB)" to remind you that this will flash the firmware using only USB. Change the field under "C/C++ Application" to `/usr/bin/make`.&#x20;

![](../../.gitbook/assets/hg\_mcuxpresso14.png)

![](../../.gitbook/assets/hg\_mcuxpresso15.png)

Also go into the "Arguments" tab and add `nxp_fmuk66-v3_default upload` into "Program arguments".

![](../../.gitbook/assets/hg\_mcuxpresso16.png)

Finally, go into the "Common" tab. Tick the checkbox in front of "Run" under "Display in favorites menu". Press apply and close the window. You can now upload firmware binaries to the FMUK66 with just the USB cable by clicking on the green "run" icon in the toolbar.

![](../../.gitbook/assets/hg\_mcuxpresso17.png)

## Debug Configurations

The next step is to also add a _debug_ configuration. This requires the J-Link EDU Mini debugger that is included with the drone kit. Make sure the debugger is plugged in to your computer and passed through to the VM ([verify that you added the J-Link debugger in the USB tab of the VM settings](virtual-machine.md#virtual-machine-settings)).&#x20;

Now in the bottom left of your screen, in the quickstart panel, press the blue bug icon with the label "Debug". Make sure that you have the right project ("HoverGames PX4") selected in the project browser on the top left!

![](../../.gitbook/assets/hg\_mcuxpresso18.png)

A new window opens and should show the attached J-Link debugger. Select it and press "OK".

![](../../.gitbook/assets/hg\_mcuxpresso19.png)

In the next screen, you should make the "Name" column a bit wider and select "nxp\_fmuk66-v3\_default.elf". If this file is not being shown, you should cancel and first build the software (you can click on the [hammer icon as mentioned previously](mcuxpresso.md#project-properties), or build "manually" [in the terminal](../building-firmware.md)).

When you have the .elf file selected, press "OK". It might start building the code and start a debug session. Wait for it to finish (there is an indicator at the bottom). Then press the "Terminate All Debug sessions" button in the top bar (the red square next to the resume and pause buttons) to stop all debugging sessions.

![](../../.gitbook/assets/hg\_mcuxpresso20.png)

We should make sure that the generated configuration is correct and make some small changes. Click on the small arrow between the green debug icon and the green run button. Go to "Debug Configurations...".

![](../../.gitbook/assets/hg\_mcuxpresso21.png)

Under "GDB SEGGER Interface Debugging", select the generated JLink configuration. It is probably called something like "HoverGames PX4 JLink PX4 FMUK66 Default". Make sure "nxp\_fmuk66-v3\_default.elf" is selected in the field under "C/C++ Application".

![](../../.gitbook/assets/hg\_mcuxpresso22.png)

In the "Startup" tab, disable the "Set breakpoint at" option. You can set your own breakpoints anywhere you want, we just don't need this default one.

![](../../.gitbook/assets/hg\_mcuxpresso23.png)

Finally, switch to the "Common" tab, and tick the checkbox in front of "Debug" under "Display in favorites menu". Press "Apply" and close the window. You can now start a debug session with the debug icon!

![](../../.gitbook/assets/hg\_mcuxpresso24.png)

## Upload PX4 firmware to FMUK66 using USB

If you want to do a clean build, press the clean button on the right side first. Then, click the hammer button to build to build the PX4 firmware for the FMUK66. You can check that the build configuration is set to "PX4 FMUK66 Default" by clicking on the dropdown menu next to the hammer icon. After you start the build process, the progress will be shown in the console at the bottom of the screen.

You can upload the firmware with the green "run" icon (not to be confused with the "resume" icon that you can use during debugging). You can again check that you have the right run configuration selected by clicking on the dropdown menu next to the run icon. Keep in mind that the FMUK66 needs to be connected via USB for this to work!

{% hint style="info" %}
If this does not work, make sure you have the FMUK66 plugged in to your computer and that there are two FMUK66 devices "passed through" to the virtual machine. One for the bootloader, and one for "normal operation".&#x20;

Also make sure that the board actually has a [bootloader installed](../../userguide/programming.md#programming-the-bootloader).
{% endhint %}

## Start a debugging session

You can start debugging by clicking the green debug icon, or open the dropdown menu next to it and select the "HoverGames PX4 JLink PX4 FMUK66 Default" configuration. You might get a popup about switching to the debug perspective, which will rearrange some panels within the MCUXpresso window. The debug perspective provides a better overview of the different debug tools. After debugging you can change back to the default view through the "Window" menu at the top.

![](../../.gitbook/assets/hg\_mcuxpresso25.png)

You can terminate the debug session by clicking on the button with the red square.

![](../../.gitbook/assets/hg\_mcuxpresso26.png)

## Learn more about MCUXpresso

Further [documentation](https://www.nxp.com/design/software/development-software/mcuxpresso-software-and-tools/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE?\&tab=Documentation\_Tab) and [videos](https://www.nxp.com/design/software/development-software/mcuxpresso-software-and-tools/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE?tab=Design\_Support\_Tab) about MCUXpresso are available on the NXP website. You will probably have to login to access some files and videos. You can [create an account for free](https://www.nxp.com/webapp-signup/register).

The "Advanced Debugging with MCUXpresso IDE" series provides a great introduction to the debugging tools in MCUXpresso. Most of the tools shown in these videos can be directly applied to debugging an FMUK66 board running PX4 Autopilot.

**Advanced Debugging with MCUXpresso IDE**

* [Part 1: Building Debugging and Direct Flashing](https://www.nxp.com/design/training/advanced-debugging-with-mcuxpresso-ide-part-1-building-debugging-and-direct-flashing:TIP-ADVANCED-DEBUG-MCUXPRESSO-IDE-1)
* [Part 2: Accessing Data and Peripherals](https://www.nxp.com/design/training/advanced-debugging-with-mcuxpresso-ide-part-2-accessing-data-and-peripherals:TIP-ADVANCED-DEBUG-MCUXPRESSO-IDE-2)
* [Part 3: Code & Data Breakpoints](https://www.nxp.com/design/training/advanced-debugging-with-mcuxpresso-ide-part-3-code-data-breakpoints:TIP-ADVANCED-DEBUG-MCUXPRESSO-IDE-3)
* [Additional ](https://www.nxp.com/design/training/advanced-debugging-with-mcuxpresso-ide-part-4-instruction-trace:TIP-ADVANCED-DEBUG-MCUXPRESSO-IDE-4)[videos](https://www.nxp.com/design/training/advanced-debugging-with-mcuxpresso-ide-part-5-freertos-task-aware-debug:TIP-ADVANCED-DEBUG-MCUXPRESSO-IDE-5) are [available](https://www.nxp.com/design/training/advanced-debugging-with-mcuxpresso-ide-part-6-swo-trace:TIP-ADVANCED-DEBUG-MCUXPRESSO-IDE-6) in this series, but are outside the scope of the HoverGames.

