# CAN transceivers

The RDDRONE-FMUK66 features two [CAN (Controller Area Network) busses](https://en.wikipedia.org/wiki/CAN\_bus). PX4 implements the [UAVCAN protocol](https://en.wikipedia.org/wiki/UAVCAN), and supports some motor controllers, sensors and GPS solutions with a CAN interface. The current HoverGames kit does not include any hardware with a CAN interface, except the FMU itself.

{% embed url="https://dev.px4.io/en/uavcan/" %}

## Connector pinout

| Pin | Signal | Voltage |
| --- | ------ | ------- |
| 1   | VCC    | +5.0V   |
| 2   | CAN H  | +3.3V   |
| 3   | CAN L  | +3.3V   |
| 4   | GND    | GND     |

## RDDRONE-FMUK66 Rev. C schematics

![](../../.gitbook/assets/c-can0.png)

![](../../.gitbook/assets/c-can1.png)

## RDDRONE-FMUK66 Rev. B schematic

{% hint style="danger" %}
Rev. B (and older boards) are **not supported** anymore. This information is left for reference.
{% endhint %}

![](<../../.gitbook/assets/CAN (1) (1).PNG>)
