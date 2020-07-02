---
description: >-
  The MCUXpresso Integrated Development Environment allows developers to edit,
  compile and debug code for many NXP microcontrollers. For HoverGames it is a
  useful tool for debugging the PX4 code.
---

# MCUXpresso

## Installing MCUXpresso

We will install MCUXpresso inside the virtual machine \(or native Linux environment\). This allows us to let MCUXpresso build the PX4 firmware, flash it to the FMUK66 and debug the code while it is running on the board. You can also install MCUXpresso on your host operating system, but we recommend to keep everything in a Linux environment unless you know what you are doing. It will save you a lot of headache.

The MCUXpresso IDE is available free of charge and can be downloaded from the NXP website, but you will need to create a \(free\) NXP account:

{% embed url="https://www.nxp.com/design/software/development-software/mcuxpresso-software-and-tools/mcuxpresso-integrated-development-environment-ide:MCUXpresso-IDE" %}

Click on the download button and login to your NXP account. The next page will show the current available releases. There is also a tab for previous releases. You should download the current release \(11.1.1 as of June 2020\), click on "MCUXpresso IDE" to continue. You will have to agree with some terms and conditions before you can download the software.

Download the `.deb.bin` file for Linux. You can directly download it using the Firefox browser in the virtual machine or you can download it on your host operating system and move it into the [shared folder](installing-ubuntu.md#shared-folders).

![](../../.gitbook/assets/hg_mcuxpresso1.png)

Assuming you have the file stored in the `~/Downloads` folder, you should first enter the command below to allow the package to be executed and installed. You should replace the last part of the filename with the right version number for your download! You can use the auto-complete feature for this by pressing the tab key. Just start typing the command below and press tab when you get to the version number in the file name.

```bash
chmod +x ~/Downloads/mcuxpressoide-xx.x.x_xxxx.x86_64.deb.bin
```

Now you can install MCUXpresso by executing the installer package, for which you again have to modify the filename to match the right version:

```bash
sudo ~/Downloads/mcuxpressoide-xx.x.x_xxxx.x86_64.deb.bin
```

You might get asked to accept an agreement \(use the arrow keys to select "Yes" and press enter\). Then wait for the installation to finish. After everything is completed, you can find the MCUXpresso application through the launcher. Look for the blue icon with the "X", or search for "MCUXpresso".

![](../../.gitbook/assets/hg_mcuxpresso2.png)

## Building and installing the Kinetis K66 SDK

The MCUXpresso IDE by default only contains SDK support for a few microcontrollers. You must install additional SDK packages for most micocontrollers. The Kinetis K66 that is found on the FMUK66 board is not available by default, so we will have to install its SDK package.

Go to the MCUXpresso SDK Builder linked below. If you **click on "Select Development Board"** you will be taken to a page where you can select the Kinetis K66 microcontroller and put together an SDK package. You might need to **login** again to your NXP account.

{% embed url="https://mcuxpresso.nxp.com/en/welcome" %}

You have to select the processor for which you want to build the SDK. The easiest is to use the search field. Just start typing **"MK66FN"** and select **"MK66FN2M0xxx18"** under processors. Then, **press the green "Build MCUXpresso SDK" button on the right**.

![](../../.gitbook/assets/hg_mcuxpresso3.png)

On the next page, select **Linux as the host operating system**, and make sure the toolchain / IDE selection is set to **"MCUXpresso"** \(or "All toolchains" if you want to use the SDK also with other tools\). You can leave the other settings at their default values, but feel free to include additional features if you want to. 

**Press the "Download SDK" button** when you are done. You might have to accept another agreement. The download should start immediately after that, but in some cases you might need to click on "Download SDK Archive". Download the SDK directly from your VM, or use the shared folder feature.

![](../../.gitbook/assets/hg_mcuxpresso4.png)

Now, start MCUXpresso within your VM. You can find it in Ubuntu's **launcher menu**. MCUXpresso will immediately ask at what location the **workspace** should be saved. You can chose your own directory, or leave the default as is. You can also create additional workspaces if you want.

You will be greeted by a welcome screen. You can **close the "Welcome" tab** or **press the "IDE" button on the top right** to continue. Once you are in the main view of the IDE, find the location were you stored the Kinetis K66 SDK .zip file, and **drag the archive** into the area of the IDE window that says "Installed SDKs". It's usually located at the bottom. It will ask you to confirm that you want to import the SDK. Just press "OK". It might take a few seconds to install.

![](../../.gitbook/assets/hg_mcuxpresso5.png)

![](../../.gitbook/assets/hg_mcuxpresso6.png)

## Create a new project for PX4

Now that MCUXpresso and the Kinetis K66 SDK are installed, we can continue and create a PX4 project. You can create a new project in MCUXpresso by going to **"File", "New", and then "Project"**. A list with different project types will appear, from which you should select **"Makefile Project with Existing Code"** under "C/C++".

![](../../.gitbook/assets/hg_mcuxpresso7.png)

You can use any project name, but for clarity we will call it "HoverGames PX4". You should select `/home/hovergames/src/px4-firmware` as the **existing code location**. This is the folder where we cloned the PX4 firmware code. Make sure that both the C and C++ languages are selected. For "Toolchain for Indexer Settings", select **"NXP MCU Tools"**. Click "Finish" to create the project.

![](../../.gitbook/assets/hg_mcuxpresso8.png)

## Project properties

Before we continue we should change some project properties. **Select the project** we just created on the left side of the screen, go to **"Project"** in the menu at the top and then select **"Properties"**. 

Go to **"MCU Settings"** under "C/C++ Build". An error _might_ pop up, complaining about invalid values. If this happens you can close the error, switch to another tab and switch back again. You should now see the same screen as shown in the image below. On this "MCU Settings" screen, select the **MK66FN2M0xxx18** under the K6x family of MCUs.

![](../../.gitbook/assets/hg_mcuxpresso9.png)

Now go to the main "C/C++ Build" tab. Uncheck "Use default build command" and change the build command to just `make`. The PX4 build scripts will take care of the specifics, we should not supply any additional arguments here.

![](../../.gitbook/assets/hg_mcuxpresso10.png)

Then switch to the "Behavior" tab. Uncheck "Enable parallel build", because the PX4 build tools also already takes care of this. Set the "Build \(incremental build\)" target to `nxp_fmuk66-v3_default` and change the "Clean" target to `distclean`. Click "Apply" to apply all changed settings.

![](../../.gitbook/assets/hg_mcuxpresso11.png)

You can click "Apply" to apply the changes, but don't close the window yet. The current configuration is named "Debug". Let's give that a more descriptive name. Click on the "Manage Configurations..." button and then choose "Rename..." to change the name. We will call it "PX4 FMUK66 Default". You can later add additional configurations if you want to play around with the build variables or if you want to build PX4 for another board, such as the [NXP UCANS32K146](https://nxp.gitbook.io/ucans32k146/).

![](../../.gitbook/assets/hg_mcuxpresso12.png)

You can press "Apply and Close" to apply the changes and close the window.

We now have a _build_ configuration that allows us to create PX4 firmware builds for the FMUK66 board. You can use the hammer icon to start a build for the selected project. If you add multiple configurations you can switch between the different profiles with the small arrow next to the hammer icon. 

Give it a try, the console at the bottom of the IDE window will show the progress of the build. Note that this might take a while if you are building PX4 for the first time! When you make changes to the code after the first build it should only rebuild the changed files.

![](../../.gitbook/assets/hg_mcuxpresso15.png)

## Run configuration

We can now build the PX4 firmware with MCUXpresso. We are now going to also add a _run_ configuration to flash the standard \(optimized\) binary directly to the FMUK66 board with just a USB cable.

{% hint style="info" %}
Flashing the PX4 firmware without a debugger is only possible [if the bootloader has already been flashed](../../userguide/programming.md) \(with a tool such as JLink Commander\).
{% endhint %}

At the top of the screen, you have a green "Run" icon. Click on the small arrow next to it, and select "Run Configurations...". In the window that opens, select "C/C++ Application" and click the "New" button above it. Name the newly created configuration "HoverGames PX4 Upload \(USB\)", and change the field under "C/C++ Application" to `/usr/bin/make`. 

Also select "Disable auto build", this will prevent the IDE from automatically building the firmware again when you try to flash your current build to the board. That also means that you always have to use the hammer icon to build the firmware yourself.

![](../../.gitbook/assets/hg_mcuxpresso16.png)

![](../../.gitbook/assets/hg_mcuxpresso17.png)

Click on the "Search Project..." button under "C/C++ Applicatoin:" to look for a binary file within the project. If you have build the firmware already it should list "nxp\_fmuk66-v3\_default.elf". If it does not, save the configuration that you are working on and first run a build.

![](../../.gitbook/assets/hg_mcuxpresso18.png)



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



