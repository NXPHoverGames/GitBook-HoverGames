---
description: >-
  The RDDRONE-FMUK66 includes three electrical fuses. They will blow when too
  much current goes through them, to protect the MCU and other components on the
  PCB.
---

# Electrical fuses

## Determining if a fuse is blown

It is easily determined if a fuse is blown by using a multimeter to measure if the fuse is still conducting. If you are certain that a fuse is blown, you will have to replace it by a similar fuse that can handle 500 mA.

{% hint style="success" %}
The fuses have **changed on recent boards** to an **automatically resetting type**. You should **never have to change them**. If they do open, simply **wait** a very brief amount of time for them to reset. However you should determine \*WHY\* the fuse opened before attempting to use the board.&#x20;
{% endhint %}

## Fuse locations

RDDRONE-FMUK66 has three fuses, two (F1 & F2) for the CAN transceivers, and one (F3) for the USB port.

![Locations of the fuses on the Rev. B board. All three fuses are located on the back of the board.](<../.gitbook/assets/nxphlite-back-fuses (1).jpg>)

## Fuses F1 & F2 (CAN transceiver)

![](<../.gitbook/assets/CAN-fuse (3).png>)

## Fuse F3 (USB port)

![](<../.gitbook/assets/usb-fuse (1).png>)

\


