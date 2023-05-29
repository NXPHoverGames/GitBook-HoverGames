---
description: >-
  The power module provides power to the FMU and has voltage and current
  sensors.
---

# FMU power module

Presently we re-use the standard power adapter from PX4 products. We are working to supply one with the correct JST-GH end already applied.

Power modules include a regulator to adapt from 2S (7.4V), 3S (11.1V), or 4S (14.8V) battery input and provide +/- 5.3V power to the FMU. Some power adapters may allow higher input voltages. In addition to power regulation it includes signals for voltage and current monitoring.

## Power distribution

This adapter also passes power through to the rest of the drone or rover platform. In addition there will typically be an additional power distribution board (PDB) to which the drive motors can be connected. A small PDB is included in the HoverGames kit, it should fit in the middle of your drone frame.

## Notes

You may have been provided a cable to adapt from the Hirose DF13 6 pin connector on the power adapter to the JST-GH 6 pin connector.

* We have noted that some of these are difficult to fit into the Hirose end.
* There may be a couple of tiny "nubs" on that connector that should be removed. Also you may want to file the connector slightly.
* It may require quite a bit of force to get the connector to push in. Be steady, and use some pliers to apply steady force after ensuring it is aligned correctly

**Advanced**: A JST-GH header can be soldered to the power adapter, allowing the used of a standard JST-GH to JST-GH straight through cable. Carefully look at the location of pin 1 as the vertical and horizontal versions of the JST-GH header swap the location of pin 1.

## Changing the power module cable

The initial power modules did not have the correct JST-GH end installed. You may need to swap the cable as shown below.

{% hint style="info" %}
This is not an optimal solution, and will be corrected in the final kits. We're not clear why the Hirose type replacement is not an exact match and needs force to install. We appreciate this is a sub-optimal situation. Please be careful when installing so as to not break the connectors or cable.

The key seems to be to carefully align and get the connector started by hand before using the pliers.
{% endhint %}

![Extra JST-GH to Hirose cable included with some early kits.](../../../.gitbook/assets/img\_20180514\_132829.jpg)

![Cut away some of the shrink wrap around the connector.](../../../.gitbook/assets/img\_20180514\_132859.jpg)

![Top: JST-GH connector. Bottom: Hirose DF13.](../../../.gitbook/assets/img\_20180514\_132936.jpg)

![Note the nubs may not align on the new cable and have to be removed.](../../../.gitbook/assets/img\_20180514\_132956.jpg)

![Use side cutters to remove the mis-matched nubs.](../../../.gitbook/assets/img\_20180514\_133132.jpg)

![Mismatched nubs also need to be removed on the other side.](../../../.gitbook/assets/img\_20180514\_133224.jpg)

![File smooth as needed with a metal or nailfile. ](../../../.gitbook/assets/img\_20180514\_133235.jpg)

![Nubs removed (top).](../../../.gitbook/assets/img\_20180514\_133401.jpg)

![Nubs removed (bottom).](../../../.gitbook/assets/img\_20180514\_133406.jpg)

![Installation may be quite tight. Carefully align and start the connector by hand.](../../../.gitbook/assets/img\_20180514\_133449.jpg)

![Once aligned by hand, use some pliers to push the connector on (no, this is not great).](../../../.gitbook/assets/img\_20180514\_133546.jpg)

![Finished assembly.](../../../.gitbook/assets/img\_20180514\_133622.jpg)
