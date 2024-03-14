# RSSI - RC Radio Advanced configuration

## Attribution

This content generously contributed by @NotBlackMagic

## **RCReceiver RSSI**

The stock firmware of the included RC receiver, the FS-iA6B, does not provide any RSSI signal feedback even though the hardware is capable of it. It is possible to enable this feature by flashing a new firmware, developed by the community: [https://github.com/povlhp/FlySkyRxFirmware](https://github.com/povlhp/FlySkyRxFirmware)

This GitHub has all the instructions necessary on how to access the programing interface of the RC receiver and how to flash the new firmware. \


{% hint style="warning" %}
Important to note here is that the stock firmware is read protected and can't be backed up before flashing this new firmware.\
You may wish to locate the original or at least the FlySky published firmware first before making this change!\
See - [https://www.flysky-cn.com/fsi6s](https://www.flysky-cn.com/fsi6s)
{% endhint %}

With the new firmware flashed, we now have the receiver RSSI signal output on SBUS Channel 14, which then can be read by the FMUK66 by setting the RC\_RSSI\_PWM\_CHANNEL parameter in the PX4 firmware (can be done through QGroundControl) as shown in the figure bellow:

Enabled RC RSSI reading on SBUS Channel 14

<figure><img src="https://hackster.imgix.net/uploads/attachments/1574633/px4_rssi_fs-ia6b_Jd8RpAwNnw.png?auto=compress%2Cformat&#x26;w=740&#x26;h=555&#x26;fit=max" alt=""><figcaption></figcaption></figure>

The RSSI value is then also displayed in QGroundControl like can be seen in the figure bellow:



<figure><img src="https://hackster.imgix.net/uploads/attachments/1574632/px4_rssi_fs-ia6b_qcontrol_QEsAa9rFtz.png?auto=compress%2Cformat&#x26;w=740&#x26;h=555&#x26;fit=max" alt=""><figcaption><p>RC RSSI signal displayed in QGroundControl</p></figcaption></figure>
