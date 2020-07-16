# HG-PX4 Example Lab 4: Running Code

## Uploading firmware to the board

You're probably wondering "how do I upload my new firmware to my board"? Well, it's a simple process, so lets go over that real quick.

### Preparing the FMU

First, you'll want to disconnect your FMU from USB on your computer. Then, navigate to the Firmware tab on QGroundControl as seen below:

![](../../.gitbook/assets/image%20%28165%29.png)

### Configuring the flash settings

Once you've navigated to this screen, go ahead and plug your FMU into your computer using the provided microUSB cable. You should see a prompt asking you which firmware you want to upload. You'll want to check the "Advanced settings" box and select "Custom firmware file..." from the dropdown box. Once you've done so, you can click OK at the top right.

![](../../.gitbook/assets/image%20%28173%29.png)

### Selecting your .px4 file and flashing

Once you click OK, a dialog to select your file will appear. You'll need to navigate to your PX4 firmware directory and go to `build/nxp_fmuk66-v3_default/`. Inside that folder you'll find an `nxp_fmuk66-v3_default.px4` file. Select this file to upload the firmware to your board.

![](../../.gitbook/assets/image%20%28167%29.png)

If the firmware upgrade successfully finished, you should see a message in the log that says "Upgrade complete." in yellow. If you didn't get that message, try recompiling PX4 and trying again. 

If you did get the "Upgrade complete." message, then you can continue in this lab guide!

## Running our code

Now that we have built our PX4 application into the firmware, it's time to run it. Once you've flashed your FMU, open up the Mavlink console in QGroundControl.

![Mavlink console in QGroundControl](../../.gitbook/assets/image%20%28166%29.png)

### Finding your program

You can run PX4/NuttX commands in the Mavlink console. To see a list of commands you can run, type "?" into the console input field.

![Runnable PX4/NuttX commands](../../.gitbook/assets/image%20%28169%29.png)

### Running your program

At the top left, you can see our new program, hg\_led! Go ahead and run it in the console to see your program run!

![hg\_led example running on FMU](../../.gitbook/assets/animated.gif)

And that's it! Next, we will go over a more advanced example, and have you try to code it yourself!

