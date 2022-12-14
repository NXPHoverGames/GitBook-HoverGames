# Automotive ethernet

The FMU has a [TJA110x](https://www.nxp.com/products/analog/interfaces/in-vehicle-network/ethernet/automotive-ethernet-phy-transceivers:ETHERNET-TRANSCEIVERS) two wire automotive ethernet ([100BASE-T1](https://en.wikipedia.org/wiki/Fast\_Ethernet#100BASE-T1)) transceiver . However, this is not yet supported by PX4. Adding driver support to PX4 and implementing the protocol might become a HoverGames task/challenge in the future.

## Connector pinout

| Pin | Signal | Voltage |
| --- | ------ | ------- |
| 1   | ENET N | +3.3V   |
| 2   | ENET P | +3.3V   |

## RDDRONE-FMUK66 Rev. C schematic

![](../../.gitbook/assets/C-ethernet.png)

## RDDRONE-FMUK66 Rev. B schematic

{% hint style="danger" %}
Rev. B (and older boards) are **not supported** anymore. This information is left for reference.
{% endhint %}

![](<../../.gitbook/assets/ethernet (1) (1).png>)
