---
description: >-
  Start developing software for the HoverGames drone by extending PX4 Autopilot
  or by controlling the flight controller using software running on a companion
  computer.
---

# Getting started

## Now it's your turn

With the "user guide" part of this GitBook we tried to show you step-by-step how to build and configure your drone. However, now it's your turn. You have to pick your own tools and make your own plans for what comes next. This "developer guide" will not be a step-by-step tutorial for writing your own software for your drone, but it should still give you some idea of where to start. We aim to provide you with all the resources that you need to start learning about the PX4 software architecture and how to extend it. 

Remember that you can always ask questions on the [PX4 Discuss forums and the PX4 Slack](../contact.md#px4-slack-and-discuss-forum) and the [PX4 GitHub](https://github.com/PX4/Firmware). Also don't forget about the [PX4 User Guide](http://docs.px4.io/master/en/index.html) and the [PX4 Developer Guide](https://dev.px4.io/master/en/index.html), they should be the first place to look for further information.

## Extending PX4 or using a companion computer

Developing new features for your HoverGames drone can be done in different ways. It is possible to add new modules directly into the PX4 Autopilot software. You can also send commands to PX4 Autopilot from a companion computer. These options will be discussed below. Note that you are free to do whatever you want. You can combine different approaches for developing your application, or come up with your own approach to realize new functionality on the drone.

Adding modules into the existing PX4 Autopilot architecture can be quite challenging, but does not require extra hardware. The Kinetis K66 on the RDDRONE-FMUK66 is a fairly powerful microcontroller, but you can't compare it to the processor in your personal computer. Resources \(RAM, processing power\) are limited and your own modules have to share this with the rest of the PX4 Autopilot software. When building more advanced applications, you might have to learn more about the PX4 software architecture and embedded software in general.

The PX4 Developer Guide has some resources that will help you get familiar with the PX4 architecture, as well as writing your first module/application within PX4.

{% embed url="https://dev.px4.io/master/en/concept/architecture.html" %}

{% embed url="https://dev.px4.io/master/en/apps/hello\_sky.html" %}

Another option is to send commands to PX4 from a companion computer that's also on the drone. Using a special adapter board, a NXP Rapid IoT Prototyping Kit can be used as a companion computer. The main advantage is that you do not have to worry as much about the already existing PX4 software architecture. You can build your application however you want without worrying that you are affecting the performance of the flight controller. However, you have to use standard MAVLink messages to communicate with PX4, which might require some creativity to get the drone to do exactly what you want.

The PX4 Developer Guide provides some information about the use of companion computers.

{% embed url="https://dev.px4.io/master/en/companion\_computer/pixhawk\_companion.html" %}

## Development tools

This developer guide provides instructions for setting up and using some [development tools](tools/). You will need them to write, build, debug and program software for PX4, RDDRONE-FMUK66 and the HoverGames drone. You can either download a preconfigured environment with most tools already installed, or you can setup your own environment from scratch \(which might be educational as well\).

## Building and programming software

We have pages that explain how to [build the bootloader](building-bootloader.md) and [firmware ](building-firmware.md)from source using the console instead of an IDE. A guide to [programming the binaries onto the FMU using the J-Link debugger](program-software-using-debugger.md) is also available.

## Resources

### Learn Git

If you have not worked with Git before, you might want to learn the basics before you continue. Git is a very popular version control system. You will probably use it a lot when developing your own software for the HoverGames drone, because the PX4 firmware is hosted on GitHub, a software hosting platform which is based on Git. 

There are many resources available online, this is just a quick selection \(in no particular order\):

* [https://git-scm.com/](https://git-scm.com/)
* [https://www.atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials)
* [https://try.github.io/](https://try.github.io/)
* [https://www.codecademy.com/learn/learn-git](https://www.codecademy.com/learn/learn-git)
* [http://gitimmersion.com/](http://gitimmersion.com/)
* [https://dev.to/unseenwizzard/learn-git-concepts-not-commands-4gjc](https://dev.to/unseenwizzard/learn-git-concepts-not-commands-4gjc)

### Learn C/C++

PX4 is mostly written in C and C++. If you are not familiar with these programming languages, it will be useful to follow a few tutorials and read about the basic concepts. There are many great books, courses and tutorials available for learning these programming languages. These are some useful websites:

* [https://isocpp.org/](https://isocpp.org/)
* [https://www.learncpp.com/](https://www.learncpp.com/)
* [https://www.codecademy.com/learn/learn-c-plus-plus](https://www.codecademy.com/learn/learn-c-plus-plus)
* [https://www.learn-c.org/](https://www.learn-c.org/)
* [https://www.learn-cpp.org/](https://www.learn-cpp.org/)

