---
description: Estimating parameters
---

# Flight time and Payload

Payload, Motors and Airframe


The HoverGames drone KIT-HGDRONEK66 doesn’t have an officially specified carry weight as it is not a product, but rather a reference or evaluation tool.

In practice – with the motors and propellers we provide – is is good for about 500g payload. People have maxed it out to almost 1Kg payload.

BUT – The motors and props can be changed to larger ones, as can the batteries and even the motor controllers. Bigger motors, bigger Carbon Fiber props and optimizing the battery size vs payload all contribute to the tradeoff between lift capacity and overall flight time.

You COULD even attach a second set of four motors facing downward.

ALSO – the size of the motors / props is limited only by the frame. All the same electronics can be moved to a larger multicopter frame. You might also just be able to use longer arms on the same frame in order to get larger propellers in place.\
\
Keep in mind these modifications will change the characteristics of the ariframe, and you will want to spend time with advanced tuning to make sure the airframe performs as expected. (PID timing, resonances etc)

There are online calculators to work out payload and estimated flight time. This is a popular one:  [https://www.ecalc.ch/xcoptercalc.php](https://www.ecalc.ch/xcoptercalc.php)

## Battery Tuning

The traditional battery current and voltage, and hence state of charge, is managed by a simple analog to digital conversion. There are scaling factors that mean you may not be getting the full energy out of your battery. In addition different batteries have different internal resistances, and react differently to temperature changes. For example, you won't get the same energy out of a battery that is operated in the cold. Some systems exist even to warm up a battery to an optimal temperature.

There are a number of things that can be done to ensure your battery readings are accurate. Follow the PX4 guide for this.

\
XXX \<Todo> created a nice youtube video that shows how to check that scaling parameters in PX4 accurately match what is happening at the battery. \


&#x20;
