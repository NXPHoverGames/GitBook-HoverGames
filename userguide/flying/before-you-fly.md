---
description: Important things to check before you fly.
---

# Before you fly

## Pre-flight and takeoff procedures <a href="#takeoff-procedure" id="takeoff-procedure"></a>

In order to start flying your drone, there are a couple of steps you need to follow. It is important to follow all these steps _before_ _**every**_ _flight_.

{% hint style="success" %}
Please use PPE - Personal Protective Equpiment such as eye protection, heavy clothing that covers exposed skin and closed toe heavy boots while working with any drone.&#x20;
{% endhint %}

1. Make sure you have **fully set up your drone**. While it is not necessary to check every little setting every time before takeoff, it is a good idea to regularly check your settings, especially after making a lot of changes.
2. Check out the [**Flying Regulations**](../../safety.md#drone-laws-and-regulations) in your area whether you are allowed to fly in your area.
3. Check that you are flying safely by going through the [**Safety Guidelines**](../../safety.md#safety-settings)**.**
4. **Arm the drone**, which is a two-step process involving both the drone and the RC transmitter:
   1. Arm on the drone-side by **pressing and holding the safety switch on the GPS module**, until it starts blinking faster.
   2. Arm on the RC transmitter-side by **holding the left stick to the bottom right**, until the safety switch and RGB LED on the FMU glow solid. _**At this point the drone is armed!**_

When the drone is armed, its motors will **start rotating immediately!** When you test this for the first time, do this **without propellers!**

![Arming switch location on the GPS module.](<../../.gitbook/assets/switch (1).jpg>)

Now that the drone is armed, it can be controlled using the RC transmitter. For more tips on things to think about while flying, you can refer to the [During flight](during-flight.md) section. When it is armed, the drone can be **disarmed** by moving the left stick on the RC transmitter to the bottom left, until the lights on the drone start flashing again (safety switch and RGB LED). More information on what to do when you are done flying can be found in the [After you fly](after-you-fly.md) section.

### Pre-flight checklist

It's a good idea to make your own pre-flight checklist and "tick off the boxes" before you arm the drone and go fly. At least include the steps that are mentioned above, with as much details as you need to remember what you need to do exactly.

You can also enable a generic preflight checklist in QGroundControl! Go to the application settings by clicking on the logo on the top left, and the enable "Use preflight checklist". When this is enabled, the home screen will show a checklist with some important steps you should perform before a flight.

![Enable the preflight checklist in QGroundControl.](<../../.gitbook/assets/image (154).png>)

## Safety

Drones are not toys, and should be handled with care to make sure no-one gets  hurt. While the local regulations mentioned above improve the general safety somewhat, taking good care of your drone is also required for a safe flight. It is important to do this before every flight, since damaged or loose components can cause the drone to malfunction during flight, leading to loss of control and crashes!&#x20;

Some general checks that apply to any custom-made drone:

* Check whether the **propellers are mounted properly**. This means that they are spinning in the right direction, and that they are mounted tightly.&#x20;
  * _**DOUBLE CHECK that the propeller nuts are tight and they have not loosened since last use.**_
* Make sure that the **propellers can rotate freely** without touching any of the frame or wiring.
* Check that there are **no loose wires** that could get in-between the propellers during flight.
* Make sure that the **battery is tightly strapped** to the frame: it should not be able to move at all. If the battery can shift during flight, it causes the drone to get out of balance, or the battery could even detach from the drone!
* Check the **battery percentage and voltage**. Flight-time can drastically decrease when taking off with a lower battery percentage. When the voltage per cell is more than 4V (total voltage for 3S = 3x4 = 12V, total voltage for 4S = 16V) there should be no problem, but when the cell voltage is below 4V you should watch your battery level extra carefully during take-off.
* Make sure that you have **correctly set up and configured all the settings** on the FMU _and_ the RC transmitter.
* Ensure you have **calibrated and tested all your sensors** before flying.

{% hint style="info" %}
PX4 contains advanced battery measurement features that allow for accurate estimation of battery percentage from measured voltage and current. More information about these features and their setup process can be found at [https://docs.px4.io/en/config/battery.html](https://docs.px4.io/en/config/battery.html)&#x20;
{% endhint %}

Drones and robots can be dangerous if safety precautions are not followed:

* **Be very careful** and follow all safety instructions and help prepare additional safety instructions and labels.
* Propellers **can and will cut severely** if not treated with respect. **NEVER** mount them until after you have calibrated and flight checked the whole system, and are ready to fly.

![Propellers WILL cut badly. Install them after the pre-flight checks, when ready to fly.](<../../.gitbook/assets/image (2).png>)

On the software side, PX4 also provides a lot of safety features, which can improve the safety of your flights. More on these safety features can be found here

{% embed url="https://docs.px4.io/en/config/safety.html" %}
