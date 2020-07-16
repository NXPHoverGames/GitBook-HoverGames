---
description: >-
  Start developing software for the HoverGames drone by extending PX4 Autopilot
  or by controlling the flight controller using software running on a (separate)
  companion computer.
---

# Getting started

## Now it's your turn

In the "user guide" part of this GitBook we showed you step-by-step how to build and configure your drone. However, now it's your turn. You have to pick your own tools and make your own plans for what comes next. This "developer guide" will not be a step-by-step tutorial for writing your own software for your drone, but it should still give you some idea of where to start. We aim to provide you with all the resources that you need to start learning about the PX4 software architecture and how to extend it. 

Remember that you can always ask questions on the [PX4 Discuss forums and the PX4 Slack](../contact.md#px4-slack-and-discuss-forum) and the [PX4 GitHub](https://github.com/PX4/Firmware). Also don't forget about the [PX4 User Guide](http://docs.px4.io/master/en/index.html) and the [PX4 Developer Guide](https://dev.px4.io/master/en/index.html), they should be the first place to look for further information.

## Extending PX4 or adding a companion computer

Developing new features for your HoverGames drone can be done in different ways. It is possible to add new modules directly into the PX4 Autopilot software. You can also send commands to PX4 Autopilot from a companion computer. These options will be discussed below. You can also keep it simple and run your software on a separate microcontroller \(or processor\) that does not communicate with the FMU, but keep in mind that this limits the usefulness of your project.

Ultimately, you are free to do whatever you want, as long as you stay within the requirements of the challenge. You can combine different approaches for developing your application, or come up with your own approach to realize new functionality on the drone. Be creative.

Adding modules into the existing PX4 Autopilot architecture can be quite challenging, but does not require extra hardware. The Kinetis K66 on the RDDRONE-FMUK66 is a fairly powerful microcontroller, but you cannot compare it to the processor in your personal computer. Resources \(RAM, processing power\) are limited and your own modules have to share this with the rest of the PX4 Autopilot software. When building more advanced applications, you might have to learn more about the PX4 software architecture and embedded software in general.

The PX4 Developer Guide has some resources that will help you get familiar with the PX4 architecture, as well as writing your first module/application within PX4.

{% embed url="https://dev.px4.io/master/en/concept/architecture.html" %}

{% embed url="https://dev.px4.io/master/en/apps/hello\_sky.html" %}

Another \(often used\) option is to send commands to PX4 from a companion computer that is also on the drone. The main advantage of a companion computer is that you do not have to worry as much about the already existing PX4 software architecture. You can build your application however you want without worrying that you are affecting the performance of the flight controller. There are some [software packages available](companion-computers.md#mavsdk) that allow you to communicate with PX4 from a companion device.

The [NavQ companion computer](https://nxp.gitbook.io/8mmnavq/) was developed by NXP with the HoverGames in mind. We recommend it for new developers that want to get started with a first companion computer. Another possible option is to use a [NXP Rapid IoT Prototyping Kit with a special adapter board](../add-ons/rapid-iot/), but note that it has "only" a Kinetis K64 microcontroller and not the powerful i.MX 8M Mini microprocessor that is available on the NavQ.

The PX4 Developer Guide provides some information about the use of companion computers.

{% embed url="https://dev.px4.io/master/en/companion\_computer/pixhawk\_companion.html" %}

{% hint style="info" %}
Technically it is possible to fully control the FMU over a wireless \(telemetry\) link. Your "companion computer" can be a powerful laptop computer if you want. However, a wireless link may not be reliable and usually does not support the high data rates that you can achieve between devices on the drone itself. Also keep in mind that mission critical commands may not reach the FMU. In general it is advised to have the companion computer on the drone.
{% endhint %}

## Development tools

This developer guide provides instructions for setting up and using the recommended [development tools](tools/). You will need them to write, build, debug and program software for PX4, RDDRONE-FMUK66 and the HoverGames drone. You can either download a preconfigured environment with most tools already installed, or you can setup your own environment from scratch \(which might be educational as well\).

## Building and programming software

We have pages that explain how to [build the bootloader](building-bootloader.md) and [firmware ](building-firmware.md)from source using the console instead of an IDE. A guide to [programming the binaries onto the FMU using the J-Link debugger](program-software-using-debugger.md) is also available.

## Learn Git

If you have not worked with Git before, you should really learn the basics before you continue. Git is a very popular version control system and you will probably have to use it a lot when developing your own software for the HoverGames drone. The PX4 Autopilot source code is hosted on GitHub, a Git-based software hosting platform. You have to use Git to retrieve the original source code, but also when you want to publish your code and contribute to the PX4 project.

The [Git source code management](git.md) page provides all the resources you need to get started with Git and GitHub. It is an essential tool and you really should spend some time on it.

## Learn C/C++

Most PX4 code is written in the C and C++ programming languages. If you are not familiar with these languages, it will be useful to follow a few tutorials and read about the basic concepts. There are many great books, courses and tutorials available for learning these programming languages.

These are some useful websites to get you started:

* [https://isocpp.org/](https://isocpp.org/)
* [https://www.learncpp.com/](https://www.learncpp.com/)
* [https://www.codecademy.com/learn/learn-c-plus-plus](https://www.codecademy.com/learn/learn-c-plus-plus)
* [https://www.learn-c.org/](https://www.learn-c.org/)
* [https://www.learn-cpp.org/](https://www.learn-cpp.org/)

These two Stack Overflow posts provide lists of the best C/C++ books:

* [https://stackoverflow.com/questions/562303/the-definitive-c-book-guide-and-list](https://stackoverflow.com/questions/562303/the-definitive-c-book-guide-and-list)
* [https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list](https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list)

