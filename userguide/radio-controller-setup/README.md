---
description: >-
  This page provides instructions on how to setup the FlySky FS-i6S RC
  transmitter that is included in the HoverGames drone kit.
---

# Radio controller setup

The FlySky FS-i6S RC transmitter is a highly configurable radio controller with a touch screen, supporting up to 10 control channels at the same time. In order to use it with the HoverGames drone, some setup is required, both for the RC transmitter and for the FMU. On this page, we will go into detail on how to set up the RC transmitter so that it can be used to safely control the HoverGames drone.

The radio controller box should include a quick start guide. A ​digital user manual for the radio controller is also available, for further information.

{% file src="../../.gitbook/assets/fs-i6s-user-manual-20170706-compressed.pdf" %}
FlySky FS-i6S User Manual
{% endfile %}

## Basic usage <a href="#setting-the-output-mode" id="setting-the-output-mode"></a>

To turn on the transmitter, press and hold the two power buttons on the front of the device until the screen lights up. After you see the logo, you will be presented with the home screen.

{% hint style="info" %}
You might see some warnings when you turn on the controller, often about default switch positions. Just follow the instructions provided on the screen to continue to the home screen.&#x20;
{% endhint %}

![The home screen of the transmitter. You see this the first time you start up the transmitter.](../../.gitbook/assets/img\_20181024\_102423.jpg)

The transmitter contains a touch screen, used for displaying status info and setup purposes. The home screen has three different views. You can switch views by swiping left and right, where the bottom indicator shows you on which screen you are (when you start the transmitter, you see the center screen).

The left screen shows you the current value sent over all channels, while the right screen shows information about sensors connected to the transmitter.

![The left home screen, showing the status of the different channels.](../../.gitbook/assets/img\_20181024\_104026.jpg)

Configuration is done by pressing the icon with the wrench and screwdriver on the center home screen. The next screen has two different views: the _function_ view and the _system_ view. The _function_ view provides options that change how the different sticks, buttons and dials on the transmitter are transformed to channel values. The _system_ view provides setting for setting up the transmitter itself.

![The function view. You can change to the system view by pressing SYS.](../../.gitbook/assets/img\_20181024\_105326.jpg)

## Firmware update

Before configuring your controller, you might want to update the firmware. Newer firmware might contain stability updates and new features that might be useful. A download link to the firmware updater tool is provided on our [downloads page](../../downloads.md#flysky-i-6-s-radio-controller-firmware-updater).

Turn on the controller and connect it to your PC using the included micro-USB cable. Go to the _system_ view in the _settings_ menu and select _firmware update_. Press the button to continue. When you start the firmware updater tool, you should see the connected controller and the current firmware version. If it is outdated, you can choose to update it.

Once the update is done, the controller should go back to normal. You should now go back into the _settings_ menu, _system_ view and select _factory reset_. This will reset all settings to the factory default. We are now ready to start changing the configuration of the radio controller.

{% hint style="info" %}
If you are annoyed by the the beeps coming from the transmitter, you can change the sound volume using the _Bri./Sound_ setting under the s_ystem_ view in the _settings_ menu.&#x20;

However, keep in mind that these sounds can also be useful. For instance, it will provide feedback when you forget to turn off the controller. It might save you some AA batteries.
{% endhint %}

## Connecting and binding the RC receiver <a href="#setting-the-output-mode" id="setting-the-output-mode"></a>

The RC receiver module [has already been installed on the drone](../assembly/escs-fmu-power-module-and-rc-receiver.md#rc-receiver-module). Please verify that it is correctly connected on both the [receiver side](../assembly/escs-fmu-power-module-and-rc-receiver.md#rc-receiver-module) and on the [FMU side](../assembly/connecting-all-fmu-wires.md#connector-pinout).

Out-of-the-box, the receiver and transmitter should be automatically bound to each other. If this is the case, the RC transmitter display would look similar to the picture below when both transmitter and receiver are turned on (receiving power). Please note the RX battery bar. If this shows a question mark (while the receiver is getting powered), the receiver pairing was most likely not done successfully.

![RC transmitter main screen.](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-LD0VYVkc6SNu1WRI9zm%2F-LD0WLWcBRtnGNEWY69M%2F20180519\_152941\_v1.jpg?alt=media\&token=e519c77c-7ef0-4155-a936-b05583c657b0)

{% hint style="info" %}
The TX battery bar shows the remaining capacity of the batteries in the transmitter. However, the **RX battery bar does NOT actually show the battery capacity of the drone**. It reports a reading of the voltage level (between 4.0 and 8.4 V) that is provided to the receiver module by the FMU, which should always be 5.0 V. In our case, it is only useful for verifying that the transmitter and receiver module are communicating.
{% endhint %}

If the transmitter and receiver are not bound, you can do it yourself. Make sure the FMU is not powered by the battery or USB cable. Insert the jumper cable in the rightmost vertical slot (labeled `B/VCC`) on the receiver module, see the picture below. The cable that goes to the FMU should remain as shown.

![The receiver module with the cable going to FMU (black/red/white) and the jumper for binding.](../../.gitbook/assets/20190807\_150917.jpg)

Turn on the RC transmitter and go to the _system_ view in the _settings_ menu. Select _RX bind_. It will wait for the receiver to be turned on in bind mode as well. You should now power the FMU, which will also power the RC receiver module. The easiest way is to power the FMU with a micro-USB cable. When power is provided, the receiver module will go into bind mode because of the jumper wire. The binding procedure should be finished automatically (you might not even notice).

**You should now pull out the binding jumper from the receiver module**. It should not remain in the receiver module, it will trigger the binding procedure again every time the receiver module is powered.

## Setting the output mode <a href="#setting-the-output-mode" id="setting-the-output-mode"></a>

In the world of drones and radio controllers,  there are a lot of different protocols that are being used. More information about these different protocols can be found [here](https://oscarliang.com/pwm-ppm-sbus-dsm2-dsmx-sumd-difference/). The FlySky FS-iA6B receiver that was included with the FlySky FS-i6S supports PWM, PPM, S.BUS and i-BUS output, but the RDDRONE-FMUK66 only supports PPM and S.BUS. For the HoverGames drone it is recommended to use the S.BUS protocol, since it is the most stable of the two and supports more channels (10 vs. 8).

Configuring the RC receiver to output the S.BUS protocol can be done in the OUTPUT MODE screen shown below. You can find the OUTPUT MODE screen on the _system_ view in the _settings_ menu. Everything should be configured as shown in the picture. This will set PPM and S.BUS as the output communication protocols, which will be available on separate pins. The FMU has already been connected to the pins on which S.BUS output will be available.

![FlySky FS-i6S settings screen for OUTPUT MODE. Set output to PPM and the serial to S.BUS.](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-LD0Zb5JCEZ4mop5guAY%2F-LD0a7uJcN6QUC07cNlp%2F20180519\_152734\_v1.jpg?alt=media\&token=69e2d94b-d972-47ba-acdd-87d49309538a)

{% hint style="warning" %}
Some changes such as enabling new RC channels to the FlySky TX or RX might reset the output mode. Check this if you no longer see RC activity in QGroundControl.
{% endhint %}

## Setting up channels on the RC transmitter <a href="#setting-up-channels-on-the-rc" id="setting-up-channels-on-the-rc"></a>

The receiver module supports up to 10 channels when using the S.BUS protocol. The first 4 channels are used to have basic control with the joysticks, leaving 6 free channels which can be mapped to auxiliary control switches. We will use these channels for changing flight modes. Assigning switches, dials and buttons on the transmitter to channels can be done using the _aux. channels_ option under the _function_ tab in the _settings_ menu. You can press the icon to change the kind of input (STx = stick, SWx = switch, VRx = dial, KEY = button). Pressing the text label you can specify which exact input should be mapped to the channel. It is also explained in section 6.7 of the manual.

The FlySky FS-i6S has 4 switches on the front, 2 dials on the top and 2 buttons on the back. All auxiliary inputs are labeled on the transmitter. For the HoverGames drone, we provide a default channel setup which allows for maximum utility of the available channels, which can be found below. In future references, we will always use the channel setup as provided here.

| Channel | Switch (SWX), dial (VRx) or button (KEY) |
| ------- | ---------------------------------------- |
| 5       | SwA                                      |
| 6       | SwB                                      |
| 7       | SwC                                      |
| 8       | SwD                                      |
| 9       | VrA                                      |
| 10      | VrB                                      |

Note that we chose to assign the two dials to channel 9 and 10. We thought these would be more useful than the two push buttons on the back of the controller. You could set up the flight controller to control a camera gimbal with these dials (please refer to the [PX4 documentation](http://docs.px4.io/master/en/index.html) or the community if you want to set this up). Feel free to reassign these two channels, we will not use them in our initial setup.

You can test the channel setup by swiping right on the home screen, and seeing whether the channel output changes when you move the inputs. You can swipe up and down to scroll through the list.

## Setting up connections loss failsafe <a href="#setting-up-connections-loss-failsafe" id="setting-up-connections-loss-failsafe"></a>

By default, when the RC receiver loses connection with the transmitter, the receiver will continue sending the latest known stick position to the FMU. While this could be useful in some situations, it is very dangerous for flying drones: it can result in fly-away situations whenever signal is lost! To change this, the _failsafe_ option in the function tab of the settings menu can be used. It allows us to set a desired value for each channel to take on whenever the RC loses connection.

{% hint style="danger" %}
Setting up proper fail-safes is **very important** for your own safety and the safety of your environment! Don't neglect this, and review your setup regularly!
{% endhint %}

While the FMU should be able to detect signal loss and has different options to react in such a situation, we also recommend a good failsafe setup on the RC transmitter, as a last resort in case the FMU does not detect the signal loss.

We recommend to set the failsafe options as follows in terms of stick and switch positions. This will cause the drone to shut down its motors when the FMU does not detect the signal loss. This is the only viable option, it is not safe to keep the drone in the air when we do not have any control over it.

We will later have a look at failsafe options in the FMU configuration as well. For now, we will set the RC transmitter failsafe to (also shown in the picture below):

* Left stick to the bottom and horizontally centered.
* Right stick both horizontally and vertically centered.
* Switches SwA, SwB and SwC in upward position, SwD in downward position.

This will set the throttle to zero and reset the yaw, roll and pitch to neutral angles. We will later assign functions to the four switches, where the upper position will be the default state. We will assign a kill switch function to switch D. With this failsafe setting, the receiver module will emulate the kill switch being flipped when it loses connection.

![The left stick should be down. The first three switches should be up. Rightmost switch should be down.](../../.gitbook/assets/img\_20181010\_131341.jpg)

To actually set up the failsafe, go to the _failsafe_ screen from the _function_ screen in the _settings_ menu. To  set up a failsafe for a channel, tap the `Off` button next to the channel. In the screen that appears, tap the `On` button to enable the fail-safe for that channel. Now make sure the stick/switch belonging to that channel is in the right position, and tap the `Setup` button to save this position.

It is also possible to set the fail-safe position for all channels at once. To do this, set all sticks and switches in their wanted fail-safe position, and press the `Set all` button to save the position of all channels. Note that you still have to **manually **_**enable**_** the fail-safe for each channel individually** after pressing the `Set all` button.

In the end, you should (approximately) have the following fail-safe values for each of the channels:

| Channel | Fail-safe value |
| ------- | --------------- |
| 1       | 0%              |
| 2       | 0%              |
| 3       | -100%           |
| 4       | 0%              |
| 5       | -100%           |
| 6       | -100%           |
| 7       | -100%           |
| 8       | 100%            |
| 9       | 0%              |
| 10      | 0%              |

{% hint style="info" %}
The exact percentages on your RC might differ a little bit. This depends on the internal stick calibration of the RC transmitter. You can re-calibrate the sticks and dials of your transmitter by using the s_ticks adjust_ setting in the s_ystem_ tab of the _settings_ menu (see section 7.6 of the manual). Note that, to complete this process, you should put both your sticks in center position after pushing them to their maximum positions. After stick calibration, you should reset the fail-safe values.

Also note that this process is not required, as the software running on the FMU will also automatically apply corrections to the RC channels. However, if the values differ more than 10% from the values given above, stick re-calibration is highly recommended.&#x20;
{% endhint %}

More information on how to set up the _failsafe_ function can be found in section 6.9 of the manual.

In the default HoverGames configuration (when following the default setup as provided in the rest of the guide), the drone will switch to manual mode with throttle all the way down and the kill-switch enabled, causing it to _crash-land_. Though it is not nice for the drone (it will crash, possibly causing damage to itself), we recommend this behavior as it prevents scenarios where the drone flies away without you being able to control it (fly-away). **You should never fly above people with these settings!**&#x20;

If you do not want the drone to crash in such situations, you could try different fail-safe settings that will keep the drone in the air. Note that this will always depend on good GPS coverage and height sensors, which makes it possible that the drone will suddenly behave unexpectedly: when GPS signal is lost, it could fly away in a random direction! When height data gets corrupted, the drone could suddenly change altitude rather quickly, which could also cause unsafe situations. Unless you really know what you are doing, **we strongly recommend you to use the provided settings**!

![Setting up a failsafe on channel 3 of -93% (throttle stick down).](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-LLEwMkEM195NTN58tEI%2F-LLF0OjGWTwmM8HChVt2%2FIMG\_20180831\_144353.jpg?alt=media\&token=3be85503-607e-492b-8944-a444483ef23a)

{% hint style="danger" %}
Again, setting up the fail-safe is **very important** for your own safety and the safety of your environment! Take the time to carefully review this page.
{% endhint %}

