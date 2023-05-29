---
description: Thanks to Andrew Brahim on YouTube!
---

# NavQ Camera Servo Mount

## Video Guide

This video is from **Andrew Brahim** on YouTube. The written guide below is an overview of what he does in the video.

{% embed url="https://www.youtube.com/watch?v=RtyZvYPTrh4" %}

## Guide

### Materials

You can purchase a servo turret like the one linked below:

{% embed url="https://www.amazon.com/Camera-Platform-Anti-Vibration-Mount-servo/dp/B00FHRVI5C/ref=sr_1_19?dchild=1&keywords=Camera+servo+turret&qid=1611691657&sr=8-19" %}

You will also want an UBEC that will power the +5V rail on the PWM channels:

{% embed url="https://www.amazon.com/Comimark-Switch-Regulator-Lowest-Noise/dp/B087NCT8RL/ref=sr_1_2?dchild=1&keywords=UBEC&qid=1611691997&sr=8-2" %}

You can mount the Pan/Tilt mount wherever you want on your drone. You may be limited in range by the length of the MIPI CSI cable that comes connected to the Google Coral Camera on the NavQ. You can purchase a longer cable from here:

{% embed url="https://www.amazon.com/Low-Voltage-Labs-Raspberry-Camera/dp/B07V7K7FNQ/ref=sr_1_1_sspa?dchild=1&keywords=MIPI+CSI+cable&qid=1611692444&sr=8-1-spons&psc=1&smid=A1UKE3B0B6VPQF&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExUjJJSkNHUzVJRDM5JmVuY3J5cHRlZElkPUEwNjAzODg3Mk1IOFRHQTRDU0VISiZlbmNyeXB0ZWRBZElkPUEwNjY1OTE4MVFHMEZUUUVJQ0dETCZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=" %}

### Hardware setup

The UBEC needs to be supplied power from the included power distribution board - you can solder the +/- wires to any of the leads on the board.

{% hint style="info" %}
This image is from the NXP Cup Gitbook, so just use this as an example. Your Power Distribution Board will have bullet connectors on it.
{% endhint %}

![](<../.gitbook/assets/image (182).png>)

Mount the Pan/Tilt mount anywhere you'd like on your drone. Plug each servo into the #5 and #6 PWM channels on the FMU, and plug the UBEC into the BEC port.&#x20;

{% hint style="info" %}
Make sure that your UBEC is set to 5V.
{% endhint %}

![](<../.gitbook/assets/image (183).png>)

### Setup in QGroundControl

These are the settings you will want to use in QGroundControl to control the servos.

![](../.gitbook/assets/screen-shot-2021-01-26-at-2.30.14-pm.png)

![](<../.gitbook/assets/image (177).png>)

![](<../.gitbook/assets/image (179).png>)

![](<../.gitbook/assets/image (180).png>)

![](<../.gitbook/assets/image (181).png>)

