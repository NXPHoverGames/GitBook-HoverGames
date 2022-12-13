# Bosch BME688


 For Hover Games 3 the partner is Bosch.  The sensor provided with the free hardware was the Adafruit BME688 module.
 https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme688/
 
 {% embed url="https://www.youtube.com/watch?v=4vdliMRtxBY&feature=youtu.be" %}

 
 This sensor is pin compatible with the BME680, but with AI built in!
 ![HoverGames 3 sensor package with Bosch BME688 ](../.gitbook/assets/BME688\_kit.jpg)
 
 
 ## Connections 
 The Adafruit BME688 module has two JST SH 4 pin sockets (Also called Qwiic/ Sparkfun QT) for I2C access to the sensor.  
 If you want to use SPI there is pads ready to solder your own connection. Use a piece of header to make it breadboard compatible
 
 
 ## Cables included with Hover Games 3 Sensor kit

* Stemma QT to Qwiic (Used by Adafruit and Sparkfun breakout boards)
 * Qwiic to open pins (useful for breadboards or some microcontrollers with sockets)
 * Qwiic to FMUK66
 * Qwiic to NavQ
 * Qwiic to NavQPlus
 ![Qwiic to Qwiic cable connecting a BME688 module to an example Adafruit QT PY micro (not included)](../.gitbook/assets/BME688\_qwiic.jpg)
 ![JST-GH connections for FMU, NavQ, and NavQPlus](../.gitbook/assets/BME688\_JST-GH.jpg)



 ## Resources 
  * [Introduction to BME688 and AI-Studio on Youtube](https://youtu.be/4vdliMRtxBY)
  * [Adafruit item page](https://www.adafruit.com/product/5046)
  * [Adafruit Learn guide for the BME680](https://learn.adafruit.com/adafruit-bme680-humidity-temperature-barometic-pressure-voc-gas) Doesn't cover the new Bosch BME AI-Studio
  * [Bosch BME688 datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme688-ds000.pdf)
  * [Bosch BME AI-Sudio](https://www.bosch-sensortec.com/software-tools/software/bme688-software/)
  * [Bosch Github repository](https://github.com/BoschSensortec)
  
