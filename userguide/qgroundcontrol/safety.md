---
description: Important safety and failsafe options.
---

# Safety

A very important step is the setup of the safety features and **fail-safe options**. Make sure to have a look at the QGroundControl documentation for this tab.

{% embed url="https://docs.qgroundcontrol.com/en/SetupView/Safety.html" %}

For safety, we again recommend you to set up a kill switch on your controller, as has already been mentioned in the [_flight modes_](radio-and-flight-modes.md) section.

It is also highly recommended to set up fail-safe features in case the connection to the RC transmitter is lost. If you followed the suggested [radio controller setup](../radio-controller-setup/#setting-up-connections-loss-failsafe), you already have a fail-safe implemented that the receiver module will trigger. It was explained as a last resort that should turn of the drone to prevent a fly-away situation. However, PX4 should also be able to detect RC connection loss (and not listen to the kill command coming from the receiver module). You can configure different fail-safe actions, that don't necessarily damage the drone.

There is not a single best setting for fail-safe options: it depends on the situation in which the drone is deployed. For example, when flying autonomously close to people, it might some times be better to just stop the motors in uncontrollable situations: when you are flying close to people, the drone might fly into them when control is lost.&#x20;

But in other situations it might be better to have the drone try to fly to a safe location before landing: when the drone is flying very high, almost above people, where a gust of wind could blow it towards and on top of someone. You should always evaluate what is best in your specific situation.

We recommend to use the **land mode** action for both the **low battery level fail-safe** and the **RC communication loss fail-safe**. The drone will try to land in its current location when the fail-safe is triggered.

{% hint style="danger" %}
Note that a fail-safe action triggered when RC connection is lost, will be canceled when a connection is re-established. That means it is not safe to hold the drone while the fail-safe is active: the motors might start spinning again! You should always first disarm the drone before picking it up (check the arming-status using either QGroundControl or the LEDs on the drone).
{% endhint %}

More information on how to set up fail-safe features can be found in the PX4 user guide:

{% embed url="https://docs.px4.io/en/config/safety.html" %}
