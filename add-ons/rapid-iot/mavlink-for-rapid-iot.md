---
description: Communication between the FMU and the Rapid-IoT
---

# MAVLink for Rapid-IOT

## Rapid IoT - Getting Started

When you are not familiar with the Rapid IoT, you can do the [Getting Started](https://www.nxp.com/support/developer-resources/rapid-prototyping/nxp-rapid-iot-prototyping-kit:IOT-PROTOTYPING?tab=In-Depth\_Tab) from the NXP website. There you can get also the [SDK ](https://www.nxp.com/webapp/sps/download/license.jsp?colCode=SLN-RPK-NODE-SDK\&appType=file1\&DOWNLOAD\_ID=null)which includes a "Hello World"-Example.

You need the both SDKs "SDK\_2.xRapidIoT\_MK64F12" and "SDK\_2.xRapidIoT\_MKW41Z4". Download them [here ](https://www.nxp.com/webapp/sps/download/license.jsp?colCode=SLN-RPK-NODE-SDK\&appType=file1\&DOWNLOAD\_ID=null)and install the SDKs by Drag\&Drop into the "Installed SDKs" window in MCUXpresso.

![](../../.gitbook/assets/GS\_Rapid\_SDKs\_edit.png)

## Setup a Rapid IoT Project

A MAVLink demo for the Rapid-IOT is available [here](https://github.com/NXPHoverGames/RapidIoT). The code includes sending and receiving messages via MAVLink using the UART2 port of the RDDRONE-IOT "HDIB" adapter board. The code bases on the "hello\_world"-application of the "SDK\_2.3.0\_RapidIoT\_MK64F12"-projects. We work with MCUXpresso.

### Import the SDK example "hello world"

In the "MCUXpresso IDE - Quickstart Panel click on the option "Import SDK example(s)..".

![](<../../.gitbook/assets/GS\_Rapid\_StartMCUX\_ImportExample\_edit (1).png>)

The "SDK Import Wizard" pops up. Here choose your board, in this case the "rapid\_iot\_k64f" and click on "Next".

![](../../.gitbook/assets/GS\_Rapid\_SDKImportWizard\_edit.png)

In the following window you can define a project name prefix and a project name suffix. In this case the default names are used.In the "Project options" choose UART as SDK Debug Console and check under the "Examples" the "hello\_world". Compare with the picture below. Now click on "Next".

![](<../../.gitbook/assets/GS\_Rapid\_SDKImportWizard2\_edit (1).png>)

In the last window uncheck the Options "Redirect SDK "PRINTF2 to C library "printf" and "Include semihost HardFault handler" and check the option "Redlib: Use floating point version of printf":

![](../../.gitbook/assets/GS\_Rapid\_SDKImportWizard3\_edit.png)

Now click on "Finish". The project will be created. This could last a moment. Build your project for the first time by using the "Build"-symbol in the upper left corner or the "Build" button in the "Quickstart Panel. (see Picture) The compiler should run without errors.

![](../../.gitbook/assets/GS\_Rapid\_StartProject\_Build\_edit.png)

We are now ready including the SDK example. Now we have to prepare the project for the MAVLink demo and then include the MAVLink Demo. First we have to activate the UART2 port in the code:

## Using UART2 on Rapid IoT

The UART2 Port is not activated jet. So we have to go the the "Peripherals". To do that select "Window" -> "Perspective" -> "Open Perspective" -> "Peripherals" or use the shortcut in the upper right corner.

![Open Perspective menu](../../.gitbook/assets/GS\_Rapid\_periph\_open\_edit.png)

Go to the Functional Group "BOARD\_Init\_TERMINAL\_UART" and scroll down to the  "UART2" Peripheral in the left menu "Peripherals". Check "UART2" and double click on the name if the menu do not open automatically. Rename the "Name" to "UART2" (instead o "UART\_1") and control if the "UART baud rate" is 115200.

![Activating UART2](../../.gitbook/assets/GS\_Rapid\_periph\_edit.png)

An error may be displayed in the functional group "BOARD\_Init\_BATSENS". If so, go to this group and open the menu for ADC0. There the input clock source is missing. Select the "Bus clock - BOARD\_Boot\_Clock\_RUN: 60 MHz" for the ADC.

![ADC0 Bus clock](../../.gitbook/assets/GS\_Rapid\_BATSENS\_edit.png)

&#x20;Now you can Update the Project via the green Button on top.  A window will pop up. Click on "OK" to update your project.

![](../../.gitbook/assets/GS\_Rapid\_periph\_updateproject.PNG)

Build your project again.&#x20;

{% hint style="danger" %}
Now, you might get errors.These are due to inconsistent makro names. At the moment there is no better solution than to adjust these makros manually. This must be done according to the following pattern:
{% endhint %}

* &#x20;Double click on an error in the "Console"

![](../../.gitbook/assets/GS\_Rapid\_UART\_error.PNG)

In one file more than one makro could be corrupt. You can identify the errors by the red underscores and the red crosses on the left side.

![](../../.gitbook/assets/GS\_Rapid\_UART\_error2.PNG)

{% hint style="warning" %}
Change only makros which are marked as errors!

NOTE: Only **one** makro per line is corrupt. If you want to see which one is incorrect, drive the mouse over the red cross. Then you will be shown which macro is corrupt.
{% endhint %}

![](../../.gitbook/assets/GS\_Rapid\_UART\_error3\_edit.PNG)

#### Example for correcting the Makros

In the picture above the makro `GPIO_INITPINS_TOUCH_RST_GPIO_PIN` is corrupt. Change this to `GPIO_INITPINS_TOUCH_RST_PIN` . \
But the makro `GPIO_INITPINS_TOUCH_RST_GPIO` is okay.  **Leave this makro as it is!**

#### **How to correct the Makros**

* Change every **incorrect** makro with `_GPIO_PIN` at the end to `_PIN` -> Delete the GPIO
* Change every **incorrect** makro with `_GPIO_PORT` at the end to `_PORT` -> Delete the GPIO
* Change every **incorrect** makro with `BOARD_INITPINS_KW41_UART_RTS_GPIO`at the end to `BOARD_INITPINS_KW41_UART_RTS_PORT`
* Change every **incorrect** makro with `BOARD_INITPINS_KW41_UART_CTS_GPIO`at the end to `BOARD_INITPINS_KW41_UART_CTS_PORT`
* Change every **incorrect** makro with `_PERIPHERAL` at the end to `_PORT`
* Change every **incorrect** makro with `_CHANNEL` at the end to `_PIN`
* Save the file and build the project again.
* Repeat these steps until there are no (new) errors anymore

If you only want to use the example, skip the next subsection and go to the section "Including the MAVLink Demo". If you want to write your own application, go further.

### Using UART2 in your own application

In your source code include the UART-Library as follows: `#inlcude "fsl_uart.h"` \
The configuration of UART2 looks like:

```c
/* UART instance and clock */
#define DEMO_UART UART2
#define DEMO_UART_CLKSRC UART2_CLK_SRC
#define DEMO_UART_CLK_FREQ CLOCK_GetFreq(UART2_CLK_SRC)
#define DEMO_UART_IRQn UART2_RX_TX_IRQn
#define DEMO_UART_IRQHandler UART2_RX_TX_IRQHandler
```

The UART2 has to be initialized first. You can do this as follows:

```c
/* Initialize UART2 */
uart_config_t config;

UART_GetDefaultConfig(&config);
config.baudRate_Bps = BOARD_DEBUG_UART_BAUDRATE;
config.enableTx = true;
config.enableRx = true;

UART_Init(DEMO_UART, &config, DEMO_UART_CLK_FREQ);
```

## Including the MAVLink Demo

Download the Repository for the [MAVLink Demo](https://github.com/NXPHoverGames/RapidIoT) and copy folder "mavlink" to your project. The file "hg\_mavlink\_demo.c" replaces the "hello\_world.c". Delete the "hello\_world.c" and copy "hg\_mavlink\_demo.c" into the "source" folder. Build your project. There should be no error. Now you can flash the code on the Rapid IoT. You can use the "GUI Flash Tool" for this. This can be found in the upper menu bar as a blue symbol.

![](../../.gitbook/assets/GS\_Rapid\_StartProject\_GUIFlashTool\_edit.png)

Use the Jlink debugger as described [here](https://nxp.gitbook.io/hovergames/developerguide/program-software-using-debugger). The program is now ready. If you want to write your own MAVLink code go further. Else skip this subsection and follow up the Section "Connecting the RDDRONE-IOT "HDIB" adapter board to the FMU" to connect your Rapid IoT device.

### Using MAVLink in your own application

Using MAVLink you need the [library](https://github.com/mavlink/c\_library\_v2). Download the project and add it as a folder "mavlink" to your project. Then include the common library in your source code as follows:

```c
#include "../mavlink/common/mavlink.h"
```

Creating a MAVLink heartbeat message is possible by using the `mavlink_msg_heartbeat_pack()`. Then the heartbeat has to be changed into a message with `mavlink_msg_to_send_buffer()` before sending. Sending the heartbeat message could be done by `UART_WriteBlocking(`). Check the example below:

```c
uint32_t tx_custom_mode = 0xffff; 							/*<  A bitfield for use for autopilot-specific flags*/
uint8_t tx_type = MAV_TYPE_QUADROTOR; 						/*<  Type of the system (quadrotor, helicopter, etc.).*/
uint8_t tx_autopilot = MAV_AUTOPILOT_PX4; 					/*<  Autopilot type / class.*/
uint8_t tx_base_mode = MAV_MODE_FLAG_MANUAL_INPUT_ENABLED; 	/*<  System mode bitmap.*/
uint8_t tx_system_status = MAV_STATE_ACTIVE; 				/*<  System status flag.*/

/* create mavlink heartbeat message and send over UART */
mavlink_msg_heartbeat_pack(1, 200, &tx_mav_msg, tx_type, tx_autopilot,
	tx_base_mode, tx_custom_mode, tx_system_status);
len_mav = mavlink_msg_to_send_buffer(send_mav_buffer, &tx_mav_msg);
UART_WriteBlocking(DEMO_UART, send_mav_buffer, len_mav);
```

With the following code you can receive a message and interpret it as a MAVLink message.

```c
/* receiving a message via UART*/
while ((kUART_TxDataRegEmptyFlag & UART_GetStatusFlags(DEMO_UART))
		&& (rxIndex != txIndex)) {
	msgReceived = mavlink_parse_char(MAVLINK_COMM_1,
			demoRingBuffer[txIndex], &message, &status);
	txIndex++;
	txIndex %= DEMO_RING_BUFFER_SIZE;
}
```

After receiving a heartbeat message can be decoded by using the function `mavlink_msg_heartbeat_decode(&message, &heartbeat)`. This function decodes the `message` and saves the result in `heartbeat`.

As another example we show you how to receive a system status message and print the voltage to the Rapid-IoT display. This works on the same principle:

```c
mavlink_sys_status_t sys_status;
mavlink_msg_sys_status_decode(&message, &sys_status);

sprintf(buff, "Voltage = %.2f V", (float)(sys_status.voltage_battery)/1000);
GUI_DispStringHCenterAt(buff, 88, 66);
```

The same procedure can be used for example receiving GPS or battery status messages. Therefore you have to replace the `sys` in the function with `gps`or `battery`. Check the source code "hg\_mavlink\_demo.c" in the project for these examples.

## Connecting the RDDRONE-IOT "HDIB" adapter board to the FMU

Mount the cable for connecting the RDDRONE-IOT "HDIB" adapter board with the FMU using UART2 as shown in the picture below.

![](../../.gitbook/assets/GS\_Rapid\_Connector.PNG)

## Using TELEM2 on FMU to communicate with the Rapid IoT

The TELEM2 Port on the FMU has to be activated first. You can do this in QGroundControl. Go to the menu "Setup", then "Parameter" and click on "MAVLink". Set the parameters as shown in the picture below. You only have to change the (red) "MAV\_1\_\*"-parameters.

![](../../.gitbook/assets/MAVLink\_Config\_angepasst.png)

Then change the Telemetry 2 baud rate to "115200 8N1" in the menu "Setup"->"Parameter"->"Serial". See red parameter in the picture below.

![](../../.gitbook/assets/MAVLink\_parameter\_serial.PNG)
