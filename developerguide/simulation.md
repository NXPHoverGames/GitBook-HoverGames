---
description: >-
  Simulators allow PX4 Autopilot to control a modeled drone in a simulated
  environment.
---

# PX4 simulation

## Why simulate?

> Simulation is a quick, easy, and most importantly, _safe_ way to test changes to PX4 code before attempting to fly in the real world. It is also a good way to start flying with PX4 when you haven't yet got a vehicle to experiment with. -- [**PX4 Developer Guide**](https://dev.px4.io/master/en/simulation/)

Many PX4 developers test their code changes in a simulator before flying a real drone with the modified software. It is much safer (and cheaper) to crash your drone in a simulator than in real-life. It is strongly recommended that you also do this if you start making changes to the PX4 firmware.

## SITL and HITL

> PX4 supports both _Software In the Loop (SITL)_ simulation, where the flight stack runs on computer (either the same computer or another computer on the same network) and _Hardware In the Loop (HITL)_ simulation using a simulation firmware on a real flight controller board. -- [**PX4 Developer Guide**](https://dev.px4.io/master/en/simulation/)

_Software-In-The-Loop_ simulation is the most used setup. It is best supported and more straightforward to use. It is actually more representative of how the software would behave in a real world flight than when using _Hardware-In-The-Loop_, because in _HITL_ several software components are being bypassed. More information is available [in the PX4 Developer Guide](https://dev.px4.io/master/en/simulation/hitl.html#hitl-vs-sitl).

{% hint style="info" %}
What the PX4 developers refer to as _Hardware-In-The-Loop_ _(HITL)_ is often called _Processor-In-The-Loop (PITL_ or _PIL)_ in industry. The term _Hardware-In-The-Loop_ is applicable when also other parts of the real hardware are being used (e.g. sensors), not just the processor with simulated inputs.
{% endhint %}

## Supported simulators

There are multiple simulators that work with PX4 Autopilot. Most simulators support SITL, some also support HITL. Gazebo is the recommended choice, it is a very powerful simulation tool and is often used together with ROS. Other options include jMAVSim and Microsoft Airsim. A complete overview and up-to-date of simulators that support PX4 is available in the [PX4 Developer Guide](https://dev.px4.io/master/en/simulation/#supported-simulators).

{% hint style="info" %}
Note - A sister competition to HoverGames uses the same hardware for cars/rovers. While still new, there may be activity available showing use of [CARLA ](http://carla.org/)for use of PX4 in an automotive simulation environment.
{% endhint %}

## Simulators in a virtual machine

Many HoverGames participants will be using a [virtual machine](tools/virtual-machine.md) for (PX4) software development. The pre-configured virtual machine does NOT come with a simulator installed and the step-by-step guide also does not explain how to setup a simulator. It is left to the user to install one if desired.

Be aware that most simulators are resource heavy and may not run very will in a virtual machine. This is especially true if your computer is not the most powerful. It is usually better to install the simulator in a native environment setup. Simulators like MS Airsim make use of gaming engines Unity and Unreal Engine for things like environmental controls, and as such the equivalent of a Gaming PC may make a good host machine.

{% hint style="success" %}
For reference: Decent results have been achieved with Gazebo on a virtual machine running Ubuntu. The virtual machine was assigned 3 processor cores of a modern quad-core Intel Core i7 with hyperthreading, and 8 out of 16 GB RAM.
{% endhint %}

## Setup instructions and further reading

The PX4 Developer Guide has a whole chapter dedicated to simulation, including some basic instructions on how to setup the simulator. It is the best resource available about simulating PX4 and it is strongly recommend that you base your simulation setup on their instructions and information:

{% embed url="https://dev.px4.io/master/en/simulation/" %}

If you have any questions or issues when using PX4 with a supported simulator, you can reach out to the PX4 community on [Discuss, Slack](https://nxp.gitbook.io/hovergames/contact#px4-slack-and-discuss-forum) or [GitHub](https://github.com/PX4/Firmware). Many people are using these simulation environments for PX4 development and it is likely that somebody will be able to help you.

Simulators can be configured for quite advanced and realistic environments including weather, automated obstacles, and wind. Typically gazebo by default is intentionally a very plain environment. You may be able to find material in the ROS project which shows methods of configuring the gazebo environment in a more rich fashion for flying drones. See the YouTube video below for a talk from Tully Foote at the 2019 PX4 Developer summit

{% embed url="https://youtu.be/WpGSrW6jhkc" %}



