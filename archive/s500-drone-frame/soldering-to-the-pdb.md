---
description: This page shows which components have to be soldered to the PDB.
---

# Soldering to the PDB

{% hint style="warning" %}
This page is **archived**. You are probably looking for the up-to-date [assembly guide](../../userguide/assembly/).
{% endhint %}

Next, we will start soldering all components onto the power distribution board (bottom plate of the frame). The top side has solder pads for ESCs, as can be seen in the picture below.

![Top side of the power distribution board (PDB) / bottom plate of the frame.](../../.gitbook/assets/pdb.jpg)

## Soldering the XT60 connector

We will start with soldering the male XT60 connector for the battery power input, because it is a bit harder to solder than the ESCs. The male XT60 connector is the one with the two metal pins on the inside, and it should have the letter "M" on its side. On the other side it should also indicate the polarity, or which side is positive (+) and which side is negative (-). This should match up with the symbols on the board.

The XT60 connector goes on top of the board and is soldered from the bottom. All other components are soldered on top. Make sure to use enough solder to make a good connection to the board.

![Soldering the connector from the bottom. More solder would be fine, as long as the pads are not shorted.](../../.gitbook/assets/pdb-xt60.jpg)

## Soldering the ESCs

After you have soldered the XT60 connector, you can add some solder to all ten soldering pads on top of the board. There are four pairs for the ESCs, and one pair on the side meant for a UBEC.&#x20;

Note that a UBEC [might not be included](../../userguide/getting-started/not-included-items.md) in your HoverGames drone kit and is not required for most setups. Instructions for installing a UBEC are provided for the sake of completeness.

![Solder added on the soldering pads on top of the power distribution board.](../../.gitbook/assets/pdb-solder.jpg)

You can now easily solder the ESCs onto the board. We chose to solder the ESCs in such a way that the long wires coming from the ESCs go to the middle of the board. Make sure that the red wire is soldered to the positive pad (+) and the black wire to the negative pad (-).

![Single ESC soldered to the board.](../../.gitbook/assets/pdb-esc.jpg)

![All four ESCs soldered.](../../.gitbook/assets/pdb-allescs.jpg)

## Soldering the UBEC

If you have a UBEC available, you can solder it in similar way to the pair of pads on the side of the board. Again, solder the wires in such a way that they point towards the middle of the board, and make sure you get the polarity right (red is positive, black is negative).

![UBEC soldered to the board.](../../.gitbook/assets/pdb-ubec.jpg)
