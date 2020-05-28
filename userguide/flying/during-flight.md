---
description: Things to keep in mind during the flight of your drone.
---

# During flight

There are multiple modes in which you can control a drone. For each of these modes, there are different things to keep in mind. Some things apply to any flight mode, while others apply only to the more advanced flight modes. More information about the different available flight modes can be found here: 

{% embed url="https://docs.px4.io/en/flight\_modes/\#multicopter" %}

## Any flight mode

* Always **watch your environment during flight**. Next to people and animals getting in your flight area, the weather is also very important. A sudden gust of wind can quickly blow your drone out of the sky, or out of sight! If you notice that you are unable to keep the drone stable, land it immediately to avoid damage to the drone or its surroundings.
* While you can technically fly a drone by yourself, it is always safer to **have someone else with you**. They can keep track of your surroundings, and watch the telemetry information of the drone, while you can be more focused on flying the drone. 
* During flight it is important to **keep track of the battery percentage** and voltage of your drone; when the voltage gets too low, the drone will become less mobile, and eventually it will crash! Note that the lower the cell voltage, the quicker the battery will deplete. Especially at a cell voltage below 3.7 V \(3S = 11.1 V, 4 S = 14.8 V\), the battery percentage will drop pretty quickly.
* When you lose control of the drone, always **make sure that it is safe to stop the motors mid-flight**; do not engage the kill switch immediately! However, when the drone is about to hurt someone, you should enable the kill switch as soon as possible.

{% hint style="danger" %}
When the **kill switch** is used to turn off the drone, be aware that the drone is **not immediately disarmed**! You have to do this manually. If you don't, and turn off the kill switch again, the motors will turn on again! 

Make sure to **leave the kill switch on** until you have disarmed the drone and unplugged the batteries.
{% endhint %}

## Assisted flight modes

Assisted flight modes are flight modes in which the drone uses more sensors in order to keep position when it does not receive any command. An example of an assisted flight mode is _altitude control_, in which the drone regulates its height in the air using a barometer or its height above the ground using a distance sensor. _Position control_ is another assisted flight mode, in which the drone also keeps its horizontal position using GPS or a flow sensor.

During assisted flight modes, more sensors are being used by the drone. When one of these sensors fails, the drone will turn on its fail-safe \([https://docs.px4.io/en/config/safety.html](https://docs.px4.io/en/config/safety.html)\) mode, which can sometimes mean that you have to manually bring the drone to the ground. This means that you should always be watching the state of the drone to be able to react appropriately. In some cases, this means switching to another flight mode!

## Autonomous flight

During autonomous flight, the drone essentially controls itself. The drone can fly missions using GPS which you can configure using QGroundControl, or you can put the drone in offboard flight mode. When in offboard flight mode, a companion computer will provide commands to the drone.

Even though the drone controls itself, this does not mean that you do not have to watch your drone: during autonomous flight you should still keep clear sight on the drone, and be ready to take over when the drone loses control of itself.

This means switching back to an assisted flight mode or to full manual mode, or flipping the kill switch. Make sure you know which modes are available and how they work, and think about what you would do in case something goes wrong.

### Offboard flight

When something goes wrong in offboard flight mode, you should first turn of the offboard flight mode. You should set up an offboard switch on your RC transmitter, so you can use the controller to decide whether you are in control, or the companion computer.

It is also possible to set up failsafe actions for when offboard mode fails, both with and without RC connection. Before flying in offboard mode, it is highly recommended to set up these offboard failsafes, to avoid non-expected behaviour during flight.

When you need to monitor or control the companion computer connected to the FMU during flight, you should also have someone else fly the drone.

More information about autonomous flight using offboard control can be found here:

{% embed url="https://docs.px4.io/en/flight\_modes/offboard.html" %}

