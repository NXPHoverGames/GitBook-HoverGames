---
description: >-
  The FMU has a servorail with six PWM outputs and a BEC input to power the 5V
  rail.
---

# Servorail

The FMU has six PWM outputs for controlling motors or servos. Please refer to the [assembly guide](../../userguide/assembly/connecting-all-fmu-wires.md#servorail) for the order in which the ESCs should be connected. Make sure to plug in the connectors in the right way. The ground wire \(black or brown\) should go on top \(closest to the board\), the signal wire \(white or yellow/orange\) on the bottom.

The servorail also has a BEC input for powering the 5V rail, which is split from the internal 5V of the FMU and thus not powered when there is no BEC connected. This is done intentionally to isolate this as a source of electrical noise coming into the FMU. Some ESCs or servos require power from the servorail, but the default ESCs included in the HoverGames kit don't need this. They are powered directly from the battery, so it is not required to connect a BEC.

![](../../.gitbook/assets/PWM_ports.PNG)

## Servo pinout

| Pin | Signal | Voltage |
| :--- | :--- | :--- |
| 1 | SIGNAL \(PWM\) | +5.0V |
| 2 | BEC INPUT | +5.0V |
| 3 | GND | GND |

## BEC pinout

| Pin | Signal | Voltage |
| :--- | :--- | :--- |
| 1 | NC | NC |
| 2 | BEC INPUT | +5.0V |
| 3 | GND | GND |

## RDDRONE-FMUK66 Rev. C schematic

![](../../.gitbook/assets/image%20%28145%29.png)

## RDDRONE-FMUK66 Rev. B schematic

{% hint style="danger" %}
Rev. B \(and older boards\) are **not supported** anymore. This information is left for reference.
{% endhint %}

![](../../.gitbook/assets/servo%20%283%29.png)



