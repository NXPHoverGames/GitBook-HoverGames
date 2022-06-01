---
description: Notes on programming with Ubuntu and ROS
---

# TechNexion PICO-PI PICO-IMX8M companion computer

{% hint style="warning" %}
This page is **archived**. You might find what you are looking for on the [NavQ GitBook](https://nxp.gitbook.io/8mmnavq/).
{% endhint %}

## Preamble

As part of our NXP drone development solutions we like to offer several options for companion computers. The i.MX 8, 8M, 8M-mini, 8M-nano and 8M+ family of processors is a good industrial fit as they are low cost and robust. There are also automotive grade processors  to consider when functional safety is required.

i.MX 8M is a QuadCore A53 + M4 with Video pipeline and H.265 (4K HDR) decoding acceleration in hardware. It is not necessarily our perfect choice for a drone companion computer, but it is fully available now. Given it is focused on video decoding, it may be the better choice for a QGC groundstation or HDR FPV goggles. With the i.MX 8M, H.264 video decoding employs a **software** Codec.&#x20;

The i.MX 8MM ("8M Mini") is better suited as a drone companion computer as it is lower power, and includes a hardware H.264 video encoder. We will use it soon when it becomes available. Despite the name "mini" it is just as capable as the 8M processing wise. The "mini" in fact refers to a silicon die shrink to a more advanced process node. The learning and development work done on an 8M is transferable to an 8MM.

This GitBook entry is intended to document in one place the resources needed for using this board for our needs. It refers to preparing the PICO-IMX8M SOM (System on Module) and corresponding PicoPi baseboard for experimentation with Ubuntu Linux and ROS

### DATE

{% hint style="warning" %}
It is expected that this document will become outdated quickly as additional resources become available.This document was last updated **January 2019**
{% endhint %}

## Reprogramming the eMMC with Ubuntu&#x20;

The procedure for getting the desired software on the processor board is a bit more involved as we are working with a SOM that uses **eMMC memory** instead of an SDCARD it is programmed while in place on the board. The benefit however is that eMMC memory is more robust than an SDCARD memory, and therefore more suitable for a high reliability long lived embedded system. Often general purpose SDCARDs can fail with regular active use within a year or two.

### TechNexion PICO-PI 8M

The SOM board we are referring to is here:

{% embed url="https://www.technexion.com/products/system-on-modules/pico/pico-compute-modules/detail/PICO-IMX8M" %}
TecnNexion PICO-IMX8M SOM (System on Module)
{% endembed %}

The base board / carrier boards we are referring to is here:

{% embed url="https://www.technexion.com/products/pico-baseboards/detail/PICO-PI" %}
TechNexion PICO-PI baseboard/carrier board
{% endembed %}

The are several complete development kits available here:

{% embed url="https://www.technexion.com/products/system-on-modules/pico/pico-evaluation-kits" %}
Technexion PICO evaluation kits
{% endembed %}

### Specific kit we are using&#x20;

{% hint style="success" %}
**The specific kit we are using** , which includes SOM + carrier board is the **PICO-PI-IMX8M-PRO**
{% endhint %}

{% embed url="https://www.technexion.com/products/system-on-modules/pico-evaluation-kits/detail/PICO-PI-IMX8M-PRO" %}
Technexion PICO-PI-IMX8M-PRO
{% endembed %}

![](<../../.gitbook/assets/image (140).png>)



### An Ubuntu image for the PicoPi 8M

TechNexion provides a download center for images for their SOMs and Baseboards. check here for the latest versions.&#x20;

{% hint style="warning" %}
Initially I was unable to find the quickstart guide an image correctly using the sorting filters on their page. they seem to have since corrected this. If in doubt, don't use the **** page filters, and instead do \<Ctrl-F> to find a word like "IMX8M" on the page.
{% endhint %}

Link below to the TechNexion download center:

{% embed url="https://www.technexion.com/support/download-center/?wpv_aux_current_post_id=78&wpv_view_count=181-TCPID78&wpv-product=pico-imx8m" %}

TechNexion provides an Ubuntu image for the Pico-Pi-IMX8M. This image was the latest available as of January 2019. Check the TechNexion FTP site for updates:

[ftp://ftp.technexion.net/demo\_software/pico-imx8m/pico-imx8m\_pico-pi-imx8m\_ubuntu-18.04\_QCA9377\_hdmi\_20181109.zip](ftp://ftp.technexion.net/demo\_software/pico-imx8m/pico-imx8m\_pico-pi-imx8m\_ubuntu-18.04\_QCA9377\_hdmi\_20181109.zip)

[ftp://ftp.technexion.net/development\_resources/development\_tools/installer/pico-imx8m\_mfgtool\_20180911.zip ](ftp://ftp.technexion.net/development\_resources/development\_tools/installer/pico-imx8m\_mfgtool\_20180911.zip)

### Boot configuration jumpers

You will need change the jumpers to the baseboard into serial bootloader mode

{% embed url="https://www.technexion.com/support/knowledgebase/boot-configuration-settings-for-pico-baseboards/" %}

Following the same instructions for the i.MX 6 boards shown here will get the image programmed.

{% embed url="https://www.technexion.com/support/knowledgebase/loading-bootable-software-images-onto-the-emmc-of-picosom-on-pico-pi/" %}

### Remarks/todo

* [ ] Include specific instructions fro i.MX8M board
* [ ] Make clear the concept of what is happening
  * [ ] use manufacturing tool to load and run a small linux image that presents the memory as a MTD device (/dev/sdb0)?
  * [ ] Find these memory devices using a linux host computer
  * [ ] use dd to copy the TechNexion Ubuntu image over the memory on the i.Mx device&#x20;

## Other Notes

* The ubuntu image is/was using the xfce desktop environment. the date was not set using ntp, and  as a result was wrong. Webpages would not load correctly, nor would apt work correctly because the time was a year off. Setting the date manually, and loading ntp using apt corrected these issues.

### Installing ROS

Follow these instructions to install ROS on the embedded i.MX 8M board :&#x20;

{% embed url="http://wiki.ros.org/Installation/Ubuntu" %}

ROS chatter example can be found here:

{% embed url="https://wiki.ros.org/ROS/Tutorials/WritingPulisherSubscriber(c%2B%2B)" %}

### Video pipeline test

Todo - test camera input using the following info:

[https://github.com/TechNexion/u-boot-edm/wiki/Test-OV5645-MIPI-CSI2-camera-for-i.mx8](https://emea01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fgithub.com%2FTechNexion%2Fu-boot-edm%2Fwiki%2FTest-OV5645-MIPI-CSI2-camera-for-i.mx8\&data=02%7C01%7Ciain.galloway%40nxp.com%7C6d4088656ade4f9ac16308d6a0e2f240%7C686ea1d3bc2b4c6fa92cd99c5c301635%7C0%7C0%7C636873293929950897\&sdata=GEJu62rLI17Wn6KwcvrytyZ%2FKN15zW1Scs5jaRnmT%2F0%3D\&reserved=0)

`# gst-launch-1.0 v4l2src io-mode=3 device=/dev/video0 ! video/x-raw,width=1280,height=720 ! kmssink`

