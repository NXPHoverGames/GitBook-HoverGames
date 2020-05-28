---
description: This page shows how the FMU is installed in its 3D printed enclosure.
---

# FMU enclosure

The FMU comes with a 3D printed enclosure, which still has to be assembled. It consists of a top part, a bottom part and a tiny reset button. 

{% hint style="info" %}
It could be that the FMU board still has stickers on top of its connectors. You should take them off before you put the FMU inside the enclosure.
{% endhint %}

![](../../.gitbook/assets/20190408_151301.jpg)

{% hint style="success" %}
You might notice that **two pins on the PWM servorail of the FMU are shorted**. This is intentional. Due to a mistake, the rightmost GND pin on the PWM servorail was not not actually connected on the PCB. This was fixed by shorting it to the GND pin next to it. This will be corrected on future boards, but it is completely fine if you see these two pins shorted together on your board.
{% endhint %}

{% embed url="https://www.youtube.com/watch?v=eEERJBx91c0" %}

First, make sure the reset button is installed inside the enclosure. It should fit in a hole in the side, next to the hole for the micro USB connector.

![Reset button installed inside the enclosure.](../../.gitbook/assets/20190408_151145.jpg)

Now, the FMU can be installed into the bottom part of the enclosure with four short screws \(7 mm\). It could be the case that you only have one type of screw with your case, which is fine as well. Just use four of the included screws and be gentle when tightening them.

![With four screws \(7 mm\) the FMU should not be able to move.](../../.gitbook/assets/20190408_151433%20%281%29.jpg)

After the FMU is installed into the bottom part, you can put the top part on and turn the whole enclosure upside down. You need two short screws \(7 mm\) and two longer screws \(about 10 mm\) to keep the two halfs together. The short screws should go in the holes close to the servorail of the FMU. The longer ones go in the holes near the SD card slot. Again, if you have only one type of screw with your case, that is fine as well. Just be gentle when tightening the screws.

{% hint style="info" %}
Once the FMU is inside the enclosure, you should **insert the microSD card**! Flight log data will be kept on this SD card and it contains very useful information for analyzing flight performance. It's also a very nice tool when you are having issues, the logs might provide some hints about what is going on.
{% endhint %}

![Long screws go near the SD card, short screws near the servorail.](../../.gitbook/assets/20190408_152531.jpg)

![](../../.gitbook/assets/20190408_152622.jpg)

