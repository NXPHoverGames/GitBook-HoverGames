---
description: >-
  This page lists the most important parts of the HoverGames User Guide to get
  you started.
---

# Getting started

This user guide should contain most information you need to get your HoverGames drone and RDDRONE-FMUK66 flying. Most pages **should be read in order**. Sometimes a link to another page or external source is provided. It is often useful to have a (quick) look at the information found on the external page before you continue reading on this GitBook.&#x20;

Also, remember that GitBook has a search function - use it to locate specific details quickly! You can find the search box on the right side at the top of the page.

{% hint style="info" %}
Questions can be asked on the [PX4 community Slack and Discuss forum](../../contact.md#px4-slack-and-forum). If anything remains unclear or if wrong information is provided, you can [contact the HoverGames team](../../contact.md#contact-the-hovergames-team).
{% endhint %}

## Important information about the HoverGames

[Read our introduction](broken-reference) to the HoverGames and RDDRONE-FMUK66 if you haven't already done so! It explains what this program is all about, and it introduces the hardware which HoverGames builds upon. Make sure to have a look at the [important must read information](../../disclaimer.md) and the [safety page](../../safety.md) before you continue!

## Check the contents of the kit!

After receiving the HoverGames kit, the first thing you should do is **check its contents**. [A list is available](drone-kit-contents.md) which explains which items **should be included** in your kit, and the **purpose** of the different components.&#x20;

Unfortunately, it is not possible to include absolutely everything you need to fly your drone in the kit. There is a short list of items you will [have to buy separately](not-included-items.md). Most importantly, the kit **does not include a battery**!

## Learn about some basic concepts

If you have never done anything with drones before, it might be a good idea to get familiar with some basic concepts first. The earlier mentioned [list of items included in the kit](drone-kit-contents.md) gives a short explanation of the different parts of a drone. The following page also introduces some of the hardware, software and other important concepts:

{% embed url="https://docs.px4.io/v1.9.0/en/getting_started/px4_basic_concepts.html" %}

This page is part of the [documentation](https://docs.px4.io/master/en/) for the [PX4 Autopilot software](https://px4.io/), which also supports the RDDRONE-FMUK66. We will also use it to set up the HoverGames drone. There is no need at this point to read about anything other than the basic concepts. We will get to the other parts after you have build your drone.

You might come across many acronyms and terminology that you are not yet familiar with. Everything should become clear as you keep on reading. If not, there are many resources available on the internet, such as these two webpages:

{% embed url="https://oscarliang.com/quadcopter-acronyms-term-glossary-word-drone/" %}

{% embed url="https://airdronecraze.com/quick-reference-guide-of-drone-terminology/" %}

## Build your drone

When you are sure nothing is missing from your drone kit, and you have become familiar with some of the basic concepts and principles, you are ready to assemble your drone! We have an [assembly guide](../assembly/) that explains how to put all the parts together. There are written instructions with pictures[ ](../../archive/s500-drone-frame/video-guide.md)available that explain how to build the frame and how to connect the electronics. Videos have been added as well.

{% hint style="warning" %}
Be careful with the carbon fiber parts of the drone frame! The edges may be sharp.
{% endhint %}

## Configure your radio controller

Make sure to properly [configure your radio controller](../radio-controller-setup.md). The controller configuration should be changed to make it more reliable and safe.

## Learn about PX4 Autopilot and QGroundControl

The RDDRONE-FMUK66 is supported by the [PX4 Autopilot software](https://px4.io/). This GitBook will explain how to install and configure it later. First, it is important to get to know this piece of software. Luckily, the PX4 community has excellent user documentation. Have a quick look at what PX4 has to offer:

{% embed url="https://docs.px4.io/master/en/" %}

The PX4 software is often setup using the [QGroundControl software](http://qgroundcontrol.com/), which can run on your Windows, Mac or Linux computer. You will use this software a lot when changing the configuration of the HoverGames drone, when calibrating sensors or even during flight to monitor your drone. They also have their own user guide available. [Install QGroundControl](../../downloads.md#qgroundcontrol) on your computer and have a look at their documentation as well:

{% embed url="https://docs.qgroundcontrol.com/en/" %}

## Install PX4 Autopilot software and configure your drone

After you have assembled the drone, you should [program the FMU for first use](../programming.md) with a **bootloader and the PX4 software**. Then you can continue with [configuring PX4 using QGroundControl](../qgroundcontrol/).

**More (advanced) information about PX4** is available in the [PX4 User Guide](https://docs.px4.io/master/en/) that has already been mentioned a few times. It is recommended to have a look at what PX4 has to offer before your first flight.

## Let's fly!

When the drone is ready, make sure to check everything is connected and working as intended!&#x20;

We have written down some important (safety) steps [before](../flying/before-you-fly.md), [during](../flying/during-flight.md) and [after](../flying/after-you-fly.md) flight, as well as some general tips on flying. Make sure to read them carefully **before your first flight**.

{% hint style="danger" %}
Be careful! The HoverGames drone is not a toy! It can cause severe damage to people or objects if not handled correctly. Be prepared and act responsibly when you fly. Also, don't forget about your own safety!
{% endhint %}

## Frequently asked questions

Running into problems? Make sure to check the [troubleshooting page](../troubleshooting.md) before asking the community for help. If you are unable to solve the problems yourself, you can get help on the [PX4 community Slack](../../contact.md#px4-slack-and-forum) (check out the [#hovergames](https://px4.slack.com/app\_redirect?channel=hovergames) channel!), as well as their [community forums](../../contact.md#px4-slack-and-forum).

## Developing your own software

Now that you have a working drone, you can start writing your own software for the drone. This GitBook provides some information to get you started. Have a look at our [developer guide](https://nxp.gitbook.io/hovergames/developerguide).

## Technical reference

This GitBook also includes a [technical reference](../../rddrone-fmuk66/schematics.md) section for the RDDRONE-FMUK66 flight controller hardware. It provides detailed schematics and pinouts for all connectors. Have a look at this section when you start developing your own software and applications for the HoverGames drone. It gives an indication of the different options you have for extending the FMU with additional hardware components.
