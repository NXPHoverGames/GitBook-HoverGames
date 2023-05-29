---
description: Details and pinout of the power input connector on the FMU.
---

# FMU power input

The FMU receives its power through this connector, coming from the FMU power module. It has two 5V and two ground wires, and one pin for the voltage sensor signal, and another pin for the signal from the current sensor. These sensors are also included in the FMU power module.

{% hint style="info" %}
The output voltage from the FMU power module is actually about 5.3V. On the FMU there is a voltage drop in the power circuit, leaving about 5.0V afterwards.
{% endhint %}

We have a separate page about the FMU power module, which provides the power to the power input.

{% content-ref url="fmu-power-module.md" %}
[fmu-power-module.md](fmu-power-module.md)
{% endcontent-ref %}

## Connector pinout

| Pin | Signal               | Voltage |
| --- | -------------------- | ------- |
| 1   | VCC                  | +5.3V   |
| 2   | VCC                  | +5.3V   |
| 3   | CURRENT SENSOR INPUT | +3.3V   |
| 4   | VOLTAGE SENSOR INPUT | +3.3V   |
| 5   | GND                  | GND     |
| 6   | GND                  | GND     |

## RDDRONE-FMUK66 Rev. C schematic

![Schematic of the power input connector on the FMU.](../../../.gitbook/assets/C-powerin.png)

![The FMU can be powered from the power input connector or through the micro USB.](../../../.gitbook/assets/C-power.png)



## RDDRONE-FMUK66 Rev. B schematic

{% hint style="danger" %}
Rev. B (and older boards) are **not supported** anymore. This information is left for reference.
{% endhint %}

![Schematic of the power input connector on the FMU.](<../../../.gitbook/assets/power\_in (2).png>)

![The FMU can be powered from the power input connector or through the micro USB.](<../../../.gitbook/assets/power (1).png>)
