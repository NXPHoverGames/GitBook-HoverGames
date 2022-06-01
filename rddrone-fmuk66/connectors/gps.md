---
description: Pinout of the GPS connector on FMU side and on the side of the GPS module.
---

# GPS

{% hint style="info" %}
The GPS provided with HoverGames is a commercial off the shelf product from Holybro.

For **developers** interested in building their own CAN connected GPS module running as a distributed processing NuttX/PX4 system, please consider a UCANS32K146-01, UCANS32K1SIC or UCANS32K1SCT module connected with a GPS module such as from UBLOX.&#x20;
{% endhint %}

RDDRONE-FMUK66 Rev. B had a conventional 6 pin GPS connector. On RDDRONE-FMUK66 Rev. C this has been replaced by the 10 pin connector used by the Pixhawk 4 and its GPS. The HoverGames drone kit will also include this GPS. The 10 pin connector also includes the pinout for an arming switch and a buzzer.

## RDDRONE-FMUK66 Rev. C connector pinout

| Pin | Signal            | Voltage |
| --- | ----------------- | ------- |
| 1   | VCC               | +5.0V   |
| 2   | UART TX           | +3.3V   |
| 3   | UART RX           | +3.3V   |
| 4   | I2C SCL           | +3.3V   |
| 5   | I2C SDA           | +3.3V   |
| 6   | SWITCH INPUT      | +3.3V   |
| 7   | SWITCH LED OUTPUT | +3.3V   |
| 8   | 3V3               | +3.3V   |
| 9   | BUZZER            | +3.3V   |
| 10  | GND               | GND     |

## RDDRONE-FMUK66 Rev. C schematic

![](../../.gitbook/assets/C-GPS.png)

## RDDRONE-FMUK66 Rev. B connector pinout

{% hint style="danger" %}
Rev. B (and older boards) are **not supported** anymore. This information is left for reference.
{% endhint %}

| Pin | Signal  | Voltage |
| --- | ------- | ------- |
| 1   | VCC     | +5.0V   |
| 2   | UART TX | +3.3V   |
| 3   | UART RX | +3.3V   |
| 4   | I2C SCL | +3.3V   |
| 5   | I2C SDA | +3.3V   |
| 6   | GND     | GND     |

## RDDRONE-FMUK66 Rev. B schematic

![](<../../.gitbook/assets/GPS (2).PNG>)

## ReadytoSky u-blox NEO-M8N GPS module pinout

This GPS module was included in some older HoverGames drone kits. For some very old kits even the pinout had to be corrected, according to the table below. Note this is different from the RDDRONE-FMUK66 Rev. B (Dronecode) pinout.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-L9GM-f4DclNfBpkkgrx%2F-L9GMBeKQOGuqrkHEM36%2FNeo-m8n.png?generation=1522857206847972\&alt=media)

The pinout below has been tested and validated with a ReadyToSky M8N generic GPS module.

| Pin on NEO-M8N | Color  | Signal  | Voltage | Pin on FMU |
| -------------- | ------ | ------- | ------- | ---------- |
| 1              | Red    | VCC     | +5.0V   | 1          |
| 2              | Black  | GND     | GND     | 6          |
| 3              | Yellow | UART RX | +3.3V   | 2          |
| 4              | Green  | UART TX | +3.3V   | 3          |
| 5              | White  | I2C SDA | +3.3V   | 5          |
| 6              | Orange | I2C SCL | +3.3V   | 4          |

![Close up of the NEO M8N Connector pinout and cable colors.](../../.gitbook/assets/IMG\_20180331\_170151.jpg)

## ReadytoSky u-blox NEO-M8N GPS module schematic

![](../../.gitbook/assets/CAB-NXPhlite-GPS-Drawing-v2.png)

![GPS module render.](<../../.gitbook/assets/CAB-NXPhlite-GPS v2.png>)
