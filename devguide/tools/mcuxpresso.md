---
description: Guide to installing and configuring MCUXpresso for HoverGames.
---

# Setting up MCUXpresso

## Installing MCUXpresso

The first step is to actually download the MCUXpresso IDE. It is available free of charge from the NXP website, but you will need to create a \(free\) NXP account. Have a look at the link below.

{% embed url="https://www.nxp.com/support/developer-resources/software-development-tools/mcuxpresso-software-and-tools/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE?tab=Design\_Tools\_Tab" %}

{% hint style="danger" %}
Newer versions of MCUXpresso use GCC 8 by default, while the PX4 toolchain includes GCC 7 and still has [issues when trying to build it with a newer GCC version](https://github.com/PX4/Firmware/issues/11410). The easiest solution is to **download MCUXpresso version 10.3.1**, which uses the right compiler by default.
{% endhint %}

Inside your VM, download the `.deb.bin` file for Linux. Assuming you have the file stored in the `~/Downloads` folder, you can install the program using the following command, which you have to modify to match the exact version you have downloaded:

You might be asked to accept an agreement. Wait for the installation to finish. After everything is done, you can find the MCUXpresso application through the launcher. You might have to search for the name, but it should show up.

```bash
sudo sh ~/Downloads/mcuxpressoide-xx.x.x_xxxx.x86_64.deb.bin
```

## Building and installing the Kinetis K66 SDK

Go to the MCUXpresso SDK webpage and press the "Select Development Board" button. You might be asked to login to your NXP account again. The SDK webpage is available here:

{% embed url="https://mcuxpresso.nxp.com/en/welcome" %}

You will be redirected to the MCUXpresso SDK Builder. Here you have to select the board or processor for which you want to build the SDK. You can use the "Search by Name" option, just start typing "MK66FN" and select "MK66FN2M0xxx18", which should be the only remaining option. Then, press the green "Build MCUXpresso SDK" button on the right.

![](../../.gitbook/assets/image%20%28125%29.png)

In the next screen, select Linux as the host operating system, and make sure the toolchain is set to MCUXpresso. You can leave the other settings at their default values. Press the "Download SDK" or "Request build" button. You may see a screen showing that the SDK is being build. You now only have to download the SDK archive \(.zip file\). You might have to accept another agreement before the download starts. Download it from inside your VM, or transport it into your VM using the shared folder.

![](../../.gitbook/assets/image%20%282%29.png)

Now, start MCUXpresso within your VM. You can find it in the launcher menu. If you open it for the first time, it might ask you where to store its workspaces. You can chose your own directory, or leave the default as is. You can check the box to make sure you are not asked about it again. Once the IDE has started, find the location were you stored the SDK .zip file, and drag the whole file into the area of the IDE screen that says "Installed SDKs". It's usually located at the bottom. It will ask you to confirm that you want to import the SDK. Just press "OK". It might take a few seconds to install.

![](../../.gitbook/assets/image%20%2872%29.png)

## Setting up a project for PX4

Inside MCUXpresso, create a new project by going to "File", "New", and then "Project". A wizard will appear, in which you should select "Makefile Project with Existing Code" under "C/C++". You can use any name, but for clarity, we will call it "HoverGames PX4". You should select `/home/hovergames/src/Firmware` as the existing code location. Make sure both the C and C++ languages are selected. For "Toolchain for Indexer Settings", select "NXP MCU Tools". Click "Finish" to create the project.

![](../../.gitbook/assets/image%20%28102%29.png)

## Project Properties

Now some project properties have to be edited. Select the project we just created on the left side of the screen, and go to "Project" and then "Properties" at the top of the screen. Go to "MCU Settings" under "C/C++ Build". It might complain about invalid values. It seems to work to switch to another tab and switch back again. On the "MCU Settings" tab, select the MK66FN2M0xxx18.

![](../../.gitbook/assets/image%20%2893%29.png)

Now go to the main "C/C++ Build" tab. The current configuration will be "Debug". Uncheck "Use default build command" and change the build command to just `make`.

![](../../.gitbook/assets/image%20%28131%29.png)

Then switch to the "Behavior" tab. Uncheck "Enable parallel build", because the PX4 build tools already takes care of this. Also, set the "Build \(incremental build\)" target to `nxp_fmuk66-v3_default`. Click "Apply" to apply all changed settings.

![](../../.gitbook/assets/image%20%28129%29.png)

At the top of the window, you can press the button "Manage Configurations...". Create a new configuration named "Default", make it a copy of "Debug". Select the newly created configuration, and make it active using the "Set Active" button.

![](../../.gitbook/assets/image%20%2873%29.png)

In the properties window, make sure "Debug" is still selected as the profile of which you are editing. Now switch to the "Environment" tab under "C/C++ Build". Add a variable named "CFLAGS" with value `O0` \(the capital letter O and a zero\). Make sure you DO NOT select the checkbox to add the variable to all configurations. After you have done this, you can press "Apply and Close", we are done in this window.

![](../../.gitbook/assets/image%20%28153%29.png)

## Run Configurations

At the top of the screen, you have a green "Run" icon. Click on the small arrow next to it, and select "Run Configurations...". In the window that opens, select "C/C++ Application" and click the "New" button above it. Name the newly created configuration "Upload", and change the "C/C++ Application" to `/usr/bin/make`. Also select "Disable auto build".

![](../../.gitbook/assets/image%20%28116%29.png)

![](../../.gitbook/assets/image%20%2845%29.png)

Also go into the "Arguments" tab and add `nxp_fmuk66-v3_default upload` into "Program arguments".

![](../../.gitbook/assets/image%20%2877%29.png)

Finally, go into the "Common" tab. Tick the checkbox in front of "Run" under "DIsplay in favorites menu". Press apply and close the window.

![](../../.gitbook/assets/image%20%2843%29.png)

## Debug Configurations

Make sure you still have the right project selected on the left. Also make sure your J-Link debugger is plugged in and correctly passed through to your VM \([verify that you added the J-Link debugger in the USB tab of the VM settings](virtual-machine.md#virtual-machine-settings)\). Now in the bottom left of your screen, in the quickstart panel, press the blue bug icon with the label "Debug". 

![](../../.gitbook/assets/image%20%2818%29.png)

A new window opens and should show the attached J-Link debugger. Select it and press "OK".

![](../../.gitbook/assets/image%20%2862%29.png)

In the next screen, you should make the "Name" column a bit wider and select "nxp\_fmuk66-v3\_default.elf". Then, press "OK". It might start building the code and start a debug session. Wait for it to finish \(there is an indicator at the bottom\), and then press the button in the top bar with the two red squares, to stop all debugging sessions. It might also give an error and stop by itself.

![](../../.gitbook/assets/image%20%2871%29.png)

We first need to change the configuration. Click on the small arrow between the green debug icon and the green run button. Go to "Debug Configurations...".

![](../../.gitbook/assets/image%20%28154%29.png)

Under "GDB SEGGER Interface Debugging", select the generated JLink configuration. Rename it to "HoverGames PX4 JLink Debug". In this same screen, make sure "nxp\_fmuk66-v3\_default.elf" is selected in the field under "C/C++ Application". Then, under "Build Configuration", select "Debug" from the dropdown menu.

![](../../.gitbook/assets/image%20%2819%29.png)

Switch to the "Common" tab, and tick the checkbox in front of "Debug" under "Display in favorites menu". Press "Apply" and close the window.

![](../../.gitbook/assets/image%20%2857%29.png)

## Upload firmware to the FMUK66

If you want to do a clean build, press the clean button on the right side first. Then, click the small arrow next to the hammer button and select "Default" to build fully optimized firmware for normal use. It will build the software, the progress will be shown in the console at the bottom of the screen.

## Upload non-optimized firmware and start debugging session

You can start debugging by clicking the green bug icon, or click on the small arrow to the right of it and select the "HoverGames PX4 JLink Debug" configuration.

![](../../.gitbook/assets/image%20%28144%29.png)

You can stop all debug sessions with the button with the two red squares.

![](../../.gitbook/assets/image%20%2817%29.png)

Further documentation and videos are available on the NXP website.

{% embed url="https://www.nxp.com/support/developer-resources/software-development-tools/mcuxpresso-software-and-tools/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE?tab=Documentation\_Tab" %}

{% embed url="https://www.nxp.com/support/developer-resources/software-development-tools/mcuxpresso-software-and-tools/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE?tab=Design\_Support\_Tab" %}



