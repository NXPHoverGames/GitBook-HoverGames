---
description: >-
  Pinout and schematic for the Telemetry 2 port, which can also be configured as
  IRDA or extra I2C bus.
---

# Serial 2 / Telemetry 2 / IRDA

On older versions of the RDDRONE-FMUK66, this port could only be used as IRDA. Since RDDRONE-FMUK66 Rev. C, it is by default configured as a free UART, which can be used as Telemetry 2 in PX4. It can still be reconfigured to use it as IRDA or as an extra I2C bus, though pull-up resistors will have to be placed by hand.

## RDDRONE-FMUK66 Rev. C connector pinout

| Pin | Signal | Voltage |
| :--- | :--- | :--- |
| 1 | VCC | +5.0V |
| 2 | UART TX | +3.3V |
| 3 | UART RX | +3.3V |
| 4 | GND | GND |

## RDDRONE-FMUK66 Rev. C schematic

![](../../.gitbook/assets/c-serial2irda.png)

## RDDRONE-FMUK66 Rev. B connector pinout

{% hint style="danger" %}
Rev. B \(and older boards\) are **not supported** anymore. This information is left for reference.
{% endhint %}

| Pin | Signal | Voltage |
| :--- | :--- | :--- |
| 1 | GND | GND |
| 2 | UART RX | +3.3V |
| 3 | VCC | +3.3V |
| 4 | IR- | +5.0V |
| 5 | IR+ | +5.0V |

## RDDRONE-FMUK66 Rev. B schematic

![](../../.gitbook/assets/irda%20%283%29.PNG)

