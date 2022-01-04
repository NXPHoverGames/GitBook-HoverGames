---
description: >-
  Examples to get you started with creating your own modules within PX4
  Autopilot.
---

# PX4 Tutorial example code

## PX4 HoverGames starter examples

Some simple examples have been created by the HoverGames team. They are available for download on our _NXP HoverGames GitHub_ in the Tutorials repository.&#x20;

You can place these examples in the `src/examples` folder of the PX4 firmware and edit the file `boards/nxp/fmuk66-v3/default.cmake` [to include these examples in the build process](https://dev.px4.io/master/en/apps/hello\_sky.html#build-the-applicationfirmware).&#x20;

{% embed url="https://github.com/NXPHoverGames/Tutorials" %}

These HoverGames PX4 starter examples are complemented with step by step tutorials:

* [PX4 Example Lab 1: uORB Subscribe](hg-px4-example-lab-1.md)
* [PX4 Example Lab 2: uORB Publish](hg-px4-example-lab-2.md)
* [PX4 Example Lab 3: Building Code](hg-px4-example-lab-3.md)
* [PX4 Example Lab 4: Running Code](hg-px4-example-lab-4.md)
* [PX4 Example Lab 5: Build your own PX4 app](hg-px4-example-lab-5.md)

## PX4 starter examples

The PX4 firmware already includes a few example applications, some of which are similar to the examples created for HoverGames. They can be found under the `src/examples` folder and should be included by default on most builds.&#x20;

{% embed url="https://github.com/PX4/Firmware/tree/master/src/examples" %}

#### PX4 Developer Guide

The PX4 Developer Guide also includes a "getting started" page for writing your first PX4 module. This is also based on some of these examples. It explains some of the basics of creating a new module, building your new code and interacting with it from the console. It also gives an introduction to using uORB, the middleware layer that allows you to communicate with other modules.

{% embed url="https://dev.px4.io/master/en/apps/hello_sky.html" %}

It is strongly recommended that you start with these examples and then slowly start exploring other parts of the software. The [PX4 Developer Guide](https://dev.px4.io/master/en/index.html) is a good place to get information and you can always ask your questions on the [PX4 Discuss or Slack](../../contact.md#px4-slack-and-discuss-forum).

## Example code for add-on hardware

Example software for add-on components used in the HoverGames is available on their own pages. You can find them by scrolling down in the menu on the left. They are listed under "Add-On Hardware".&#x20;
