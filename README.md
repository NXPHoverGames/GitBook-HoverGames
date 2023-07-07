---
description: >-
  Welcome! This GitBook serves as the official documentation for the NXP
  HoverGames drone development kit, including the RDDRONE-FMUK66 flight
  management unit (also referred to as NXPhlite).
---

# HoverGames

{% hint style="success" %}
Also have a look at some of the other **NXP GitBooks.** These solutions all work together and can contain useful cross-linked information and example applications:\


* [NavQPlus (NavQ+) Companion Computer](https://nxp.gitbook.io/8mpnavq/) - (New!)
* [MR-CANHUBK344](http://localhost:5000/o/-L9GLsni4p7csCR7QCJ8/s/twBzyvivLuBKj9SMDwV9/) - VMU and T1<->CAN (New!)



* [UCANS32K146:](https://nxp.gitbook.io/ucans32k146/) CAN-FD / UAVCAN node
* [RDDRONE-T1ADAPT ](https://nxp.gitbook.io/rddrone-t1adapt): T1 Ethernet Adapter



* [RDDRONE-BMS772 ](https://nxp.gitbook.io/rddrone-bms772/): Battery Management System



* [NXP Cup Car](https://nxp.gitbook.io/nxp-cup-hardware-reference-alamak/) : Including [MR-Buggy3](https://nxp.gitbook.io/nxp-cup/mr-buggy3-developer-guide/mr-buggy3-build-guide) build guide&#x20;
* [El Mandadero](https://nxp.gitbook.io/elmandadero/): NXP Mobile Robotics demo rover&#x20;
* [NXP-AIM](https://nxp.gitbook.io/nxp-aim/) : Robotics competition like NXP-CUP (india) \
  \
  Older:
* [NavQ Companion Computer](https://nxp.gitbook.io/8mmnavq/) (As used in HoverGames2)
* [D2X Reference Design](https://nxp.gitbook.io/d2x/)\

{% endhint %}

![](.gitbook/assets/hg\_logo.png)

{% hint style="success" %}
See the [NXP Mobile Robotics Community ](https://community.nxp.com/community/mobilerobotics)for interactive questions and answers on NXP.com. There is a space for [HoverGames](https://community.nxp.com/community/mobilerobotics/hovergames-drone-challenge) as well as a subspace specifically for the [NavQ Companion Computer](https://community.nxp.com/community/mobilerobotics/hovergames-drone-challenge/navq-8mmnavq-discussion).\
\
Discord:\
There are also Discord channels where NXP Mobile Robotics are discussed during various competitions like HoverGames and NXP-CUP. You are welcome to ask questions there even if you may not be actively participating at the time, however it may take time before questions are noticed if there is not an active contest.\
\
NXP-CUP: [https://discord.gg/tRrASaqXrU](https://discord.gg/tRrASaqXrU)\
NXPHoverGames on Hackster.op: [https://discord.gg/upTxAs3DwP](https://discord.gg/upTxAs3DwP) \
NXP-AIM (india): (Need link to channel)
{% endhint %}

## What is this program? <a href="#what-is-this-program" id="what-is-this-program"></a>

Unmanned aerial vehicles (UAVs) promise new perspectives on the world around us and the ability to go places that were once impossible. NXP is a trusted leader in automotive, radar, aerospace, RF, security, motor control and battery management and places the world’s most complete portfolio of UAV technologies in the hands of developers. Our automotive grade solutions are well suited to the design methodology and environments in which commercial unmanned aircraft systems, and increasingly also personal UAVs, operate. We provide semiconductor solutions for every aspect of drones and rovers.

### The HoverGames drone kit

The HoverGames drone kit is a single, modular, and flexible NXP development platform with the RDDRONE-FMUK66 flight management unit at its base. It can be used to build any autonomous vehicle, from drones to rovers to flying cars. As part of the kit, participants receive a complete reference drone including the flight management unit (FMU).

{% hint style="success" %}
NXPhlite was the working name for the NXP RDDRONE-FMUK66 flight controller. You might still find references to it on older pages. We usually refer to it now as FMUK66.

The actual [NXP part numbers](https://www.nxp.com/applications/solutions/industrial/aerospace-and-mobile-robotics/uavs-drones-and-rovers:HOVERGAMES-DRONES-ROVERS) are:

* [KIT-HGDRONEK66](https://www.nxp.com/applications/solutions/industrial/aerospace-and-mobile-robotics/uavs-drones-and-rovers/nxp-hovergames-drone-kit-including-rddrone-fmuk66-and-peripherals:KIT-HGDRONEK66) - Complete drone development kit including RDDRONE-FMUK66
* [RDDRONE-FMUK66](https://www.nxp.com/design/designs/px4-robotic-drone-fmu-rddrone-fmuk66:RDDRONE-FMUK66) - NXP flight controller with the 180 MHz Kinetis K66



For full functionality of the kit, you will need to purchase a telemetry radio set separately.&#x20;

_Note that in HoverGames the discount code includes a corresponding discount for the Telemetry radio, but it still needs to be purchased/put in the shopping basket as a separate line item._

\
&#x20;Depending on your location, you need either a 915 MHz or 433 MHz set. [Please check which frequencies / ISM bands you are allowed to use in your region.](http://ardupilot.org/copter/docs/common-telemetry-radio-regional-regulations.html)

* [HGD-TELEM915](https://www.nxp.com/part/HGD-TELEM915) - Holybro 915 MHz telemetry radio set (Americas)
* [HGD-TELEM433](https://www.nxp.com/part/HGD-TELEM433) - Holybro 433 MHz telemetry radio set (Europe, India)



Other NXP flight management units, drone development kits and equipment will have similar naming conventions as they are introduced.
{% endhint %}

![KIT-HGDRONE-K66, using a Kinetis K66 ARM Cortex-M4 MCU.](.gitbook/assets/hg\_dronekit\_k66.jpg)

### HoverGames drone flight management unit (FMU)

RDDRONE-FMUK66 is an experimental flight management unit that is compliant with [Dronecode](https://www.dronecode.org/) and [PX4 Autopilot](https://px4.io/) software. PX4 is used extensively for research and commercial drone platforms. Its permissive BSD license preserves the ability to include proprietary IP.

The RDDRONE-FMUK66 runs [NuttX](https://nuttx.apache.org/) RTOS on a [NXP Kinetis K66](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/kinetis-cortex-m-mcus/k-seriesperformancem4/k6x-ethernet/kinetis-k66-180-mhz-dual-high-speed-full-speed-usbs-2mb-flash-microcontrollers-mcus-based-on-arm-cortex-m4-core:K66\_180) microcontroller, with an ARM Cortex-M4 core at 180 MHz and 2 MB flash memory. It uses NXP sensors, automotive [CAN](https://en.wikipedia.org/wiki/CAN\_bus) bus transceivers, as well as the new **two wire** automotive [100BASE-T1 ethernet](https://en.wikipedia.org/wiki/Fast\_Ethernet#100BASE-T1) transceiver [TJA110x](https://www.nxp.com/products/analog/interfaces/in-vehicle-network/ethernet/automotive-ethernet-phy-transceivers:ETHERNET-TRANSCEIVERS).

{% embed url="https://www.youtube.com/watch?v=JDaJ5Kr6aBA&feature=youtu.be" %}

## What is our mission? <a href="#what-is-our-mission" id="what-is-our-mission"></a>

### **Spread the latest technology to developers** <a href="#spread-latest-technology-to-developers" id="spread-latest-technology-to-developers"></a>

Drones and rovers have the capability to enhance our cities and rural areas in the same way that autonomous cars and mobile technologies do. We want to bring the latest innovations in these areas to the small autonomous vehicles of the future. They need the same high reliability, security and functional safety that make it possible to occupy the same spaces, roads and sky, as we humans do.

With the HoverGames challenges we can introduce this technology to you, and share our findings as we learn together how the technology could be used in new ways. We want to invite everyone who is interested to use the newest technology on the market and take advantage of the many possibilities the tech provides.

### **Co-creation code sourcing** <a href="#co-creation-code-sourcing" id="co-creation-code-sourcing"></a>

Many drone challenges today are human operated races, and while they are lots of fun, they are about operating a drone, not controlling or programming a robot. HoverGames will encourage participants to write code that enhances or activates new features in their vehicles, in addition to fun racing challenges. Ongoing coding challenges of all levels will be presented, and the resulting code is shared and published as open-source. The [PX4 community Slack, Discuss forum](contact.md#px4-slack-and-forum), [GitHub](https://github.com/PX4/Firmware) and the GitBook platforms give participants the ability to communicate and support each other as well as get support from NXP Industrial and Automotive and from external partners.

### **Tackle real life problems** <a href="#tackle-real-life-problems" id="tackle-real-life-problems"></a>

The result of solving a set of ongoing coding enablement challenges, be it for enabling new hardware components or new software features, is to use the sum of all these new capabilities to take on complex action challenges where participants design and adapt their vehicles to tackle a real societal problem. Each one is different and can range from cleaning up the beach, mapping a dangerous gas emission, or locating and tracking migration patterns of an endangered animal species.

## How do we make this mission a reality? <a href="#how-do-we-make-this-mission-a-reality" id="how-do-we-make-this-mission-a-reality"></a>

To achieve these goals, we will have a series of developer and hacker challenges.

HoverGames are a series of hands-on challenges for engineers and tech enthusiasts to co-pioneer with NXP and design for new forms of mobility. Each game consists of a set of challenges. Participants need to buy a kit - a physical complete drone kit you hold in hands - form teams and enroll virtually. As part of each game, participants will write code that activates their vehicles.

To warm up - participants will be asked to take part in comparably simple coding challenges to get familiar with their drone and the [Dronecode](https://www.dronecode.org/) environment including [PX4](https://px4.io/) software flight stack . This code serves as a basis for further challenges as they build upon each other.

After getting comfortable with the entry level challenges, participants can enroll in any of the currently active Virtual Software challenges. Some will be open to anyone, some will need pre-qualification in order to get access to specific hardware boards that might be needed.

Once or twice a year larger Societal Challenges will be announced. For these, the participants use the existing and newly solved body of knowledge to design vehicles that can solve a societal problem – For example a simulation of cleaning up nuclear waste, or tracking migration patterns of an endangered animal species.

{% hint style="success" %}
**HoverGames**: Build your drone kit with leading edge technology - _navigation, AI, environmental sensors, connectivity, functional safety and security -_ and start programming!
{% endhint %}

## We need you! <a href="#we-need-you" id="we-need-you"></a>

UAVs have a wide range of applications in many fields like environmental hazards monitoring, traffic management and pollution monitoring, all of which contributes greatly to the development of any city and rural area. HoverGames will be of great benefit to developers around the world to jointly develop autonomous robot vehicle solutions.

More information can be found on [HoverGames.com](https://www.hovergames.com/). It is also possible to directly contact the HoverGames team, contact information is available on our [contact page](contact.md#contact-the-hovergames-team).

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)\
This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
