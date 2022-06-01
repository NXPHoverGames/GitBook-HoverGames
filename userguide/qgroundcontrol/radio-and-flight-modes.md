---
description: >-
  How to set up the connection with your RC transmitter and configure different
  flight modes.
---

# Radio and flight modes

## Radio setup

In the _Radio_ tab, you only need to perform the calibration. Press the calibrate button and follow all instructions. The graph on the right side of the screen shows which stick you need to move! After the calibration is done, make sure that you see all the channels on the right of the screen move according to the movement of your sticks, switches and dials.&#x20;

More information is available in the QGroundControl User Guide:

{% embed url="https://docs.qgroundcontrol.com/en/SetupView/Radio.html" %}

![Press the "Calibrate" button to start radio calibration!](<../../.gitbook/assets/image (152).png>)

## Flight modes

After the radio calibration is done, you can continue with setting up _Flight Modes_, which has its own tab. Have a quick look at the QGroundControl documentation to know what flight modes are available:

{% embed url="https://docs.qgroundcontrol.com/en/SetupView/FlightModes.html" %}

For setting up flight modes, you are free to assign the different switches to different functions. We provide a default way of setting up the switches, which should cover most of the use cases and safety features. It includes manual and assisted flight modes, as well as offboard mode for autonomous flight and a kill switch. The mapping is based on the RC channel mapping given in the [_radio controller setup_](../radio-controller-setup.md#setting-up-channels-on-the-rc) section. Below you can find a screenshot displaying the default configuration we recommend.

![Mapping of the different flight modes, using the default transmitter channel mapping.](<../../.gitbook/assets/image (158).png>)

We recommend to use channel 6 (switch B) to switch between flight modes. Switch B is a three way switch, which correspond to flight modes 1, 4 and 6. We suggest to setup the manual, altitude and position modes to get started.

You should also assign a kill switch channel. You should use channel 8 (switch D), because you easily reach it when something goes wrong. Our [last resort RC receiver fail-safe](../radio-controller-setup.md#setting-up-connections-loss-failsafe) was also set with a kill switch on channel 8 in mind.

Channel 5 (switch A) is a nice switch for the loiter (hold) mode. When you flip this switch, the drone will stay in the same position until you switch it back.

That leaves switch C (channel 7), which is a three-way switch. You can leave it unassigned, or have a look at the other available flight modes. The choice is up to you. We have assigned the offboard mode, which allows the drone to be controlled by software running on a companion computer. If you are not sure what mode to assign, just leave it unassigned.

To recap, with this mapping switch A will put the drone in "hold mode". Switch B can be used to change between different flight modes. Switch C either remains unused, or is used to toggle offboard mode or another mode that you assigned to it. Switch D is the kill switch. Remember this, in case something goes wrong you need to be able to quickly change between flight modes or shut down the drone!

{% hint style="danger" %}
If you are making changes to this setup, you should make sure to **always** include a **kill switch** for safety! Also adapt the [RC receiver fail-safe](../radio-controller-setup.md#setting-up-connections-loss-failsafe) according to your assigned functions, the provided configuration is based on the kill switch being assigned to switch D.
{% endhint %}

