---
description: >-
  Breakout board that exposes the different interfaces from the DCD-LZ
  connector.
---

# DCD-LZ breakout board

In order to work with the DCD-LZ interface you will need a small breakout board which allows you to easily plug in each connector for all devices. The HoverGames kit includes a small board made by NXP which has a 10 pin SWD connector for Segger J-Link debuggers, a USB-TTL-3V3 header. There is also an unused "Landzo" 4 pin serial connector.

{% hint style="danger" %}
Pin 1 (black) of USB-TTL-3V3 is marked with a black dot on the DCD-LZ-ADAPT board. There is a corresponding dot marking pin 1 on top of the 3D printed case.
{% endhint %}

![Typical debugging setup.](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-L9GM-f4DclNfBpkkgrx%2F-L9GM7GAEPJoh7eLqkc4%2FIMG\_20180304\_151908.png?generation=1522857193564152\&alt=media)

## Pinout

| DCD-LZ pin | Signal | Voltage | USB-TTL-3V3 pin / color | J-Link EDU Mini pin |
| ---------- | ------ | ------- | ----------------------- | ------------------- |
| 1          | VCC    | +3.3V   |                         | 1                   |
| 2          | TX     | +3.3V   | 5 / Yellow              |                     |
| 3          | RX     | +3.3V   | 4 / Orange              |                     |
| 4          | SWDIO  | +3.3V   |                         | 2                   |
| 5          | SWCLK  | +3.3V   |                         | 4                   |
| 6          | RST    | +3.3V   |                         | 10                  |
| 7          | GND    | GND     | 1 / Black               | 3                   |

## Schematic

{% hint style="info" %}
Note that FTDI USB-UART cable presents 5V on pin3. There were originally two forward dropping diodes to feed this forward to the rest of the PCB. They have subsequently been removed in newer revisions and therefore it should be noted that JP1 pin 3 does not connect to 3V3 nor to to Pin1 of the DCD-LZ connector. An updated schematic is pending here.
{% endhint %}

![](<../../../.gitbook/assets/afbeelding (12).png>)

## JTAG/SWD 10 pin <a href="#jtag-swd-10-pin" id="jtag-swd-10-pin"></a>

The 10 pin connector is small 0.050" pin spacing connector. This is found on the J-Link EDU Mini.

Note that this is officially referred to as a 9 pin connector since the specification calls for a keying plug to be used to block pin 7, over time this seems to have become less common.

![10 pin SWD connector pinout.](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-L9GM-f4DclNfBpkkgrx%2F-L9GMBEOORUlGQBrASjn%2FJTAG-SWD-mini10.png?generation=1522857203295351\&alt=media)

## USB-TTL-3V3 pinout

{% hint style="info" %}
The USB-TTL cable really must be a 3.3V one. A cable made by FTDI or an equivalent cable should be included in the HoverGames kit. The kit also includes a Segger J-Link EDU Mini debugger, the breakout board and cable to connect it to the FMU.\
\
FTDI cables can also be bought from:

* [Mouser](https://www.mouser.com/productdetail/ftdi/ttl-234x-3v3?qs=sGAEpiMZZMve4%2FbfQkoj%2bFhARuukVcFaKCv8i%2bT7B8g%3D)​
* ​[DigiKey](https://www.digikey.com/products/en/cable-assemblies/smart-cables/468?k=FTDI+3v3\&k=\&pkeyword=FTDI+3v3\&pv167=804\&FV=ffe001d4\&mnonly=0\&ColumnSort=0\&page=1\&quantity=0\&ptm=0\&fid=0\&pageSize=25)
{% endhint %}

![](../../../.gitbook/assets/Utech-Drawing-USB-TTL-FTDI-CABLE3.3V-1.8Meter.png)

## Thingiverse case

A small case for this board has been created that can be 3D printed. The case includes an orientation mark for the ground pin of the FTDI cable and a shape which helps correct orientation of the Landzo serial port. The case should be included with the HoverGames kit, and the model is available on [its own page](../../../userguide/replacement-parts-alternatives-and-upgrades/3d-printable-parts.md#debugger-adapter-board-case).

![The location of the ground pin of the FTDI cable is marked on the casing.](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-L9GM-f4DclNfBpkkgrx%2F-L9GM7G26YBESJGbSKV0%2FIMG\_20180304\_124705.png?generation=1522857193565406\&alt=media)

## Cable between FMU and breakout board

The cable is just a 7 pin JST-GH straight through cable.

![](../../../.gitbook/assets/DCD-LZ-7pin-JSTGH-render.png)

![](<../../../.gitbook/assets/CAB-NXPhlite-DCD-LZ v2.png>)

##
