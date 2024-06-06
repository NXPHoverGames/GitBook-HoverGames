# DRVEGRD 152

## Introduction

The [DRVEGRD 152](https://www.smartmicro.com/automotive-radar/drvegrd-line#c20140) is a 76-77GHz radar sensor from the company s.m.s, smart microwave sensors GmbH. It is suitable for a wide range of automotive applications that features 4D/PxHD technology.\
The sensor has a medium and a long range mode. The medium range is up to 65 meters and the long range up to 178 meters.

## Prerequisites

The following items are required to reproduce the following setup instructions.

* Windows Device
* DRVEGRD 152
* Plug & Play cable (Alternatively, you can make the cable yourself. The connection is described in the Customer Interface.)
* CAN to USB Adapter
* NavQPlus &#x20;
  * The NavQPlus should be [set up](https://nxp.gitbook.io/navqplus/navqplus-user-guide/setup-guide-emmc) with the recommended latest [image](https://github.com/rudislabs/navqplus-create3-images)
  * A configured [ROS2 Workspace](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html) is required. The example tutorial package is not required.
* Install and download the following software and documents on your PC
  * From the smartmicro [Partner Zone](https://www.smartmicro.com/partner-zone) (requires access data):&#x20;
    * Drive Recorder Software
      * Firmware Bundle
        * CANSpec (.csdx)
          * DriveRecorder setup (.dsk)
          * Customer Interfce (User Manual)
          * Ethernet Interface (User Manual)
          * Firmware
  * PEAK Device Driver Setup for the CAN-Interface

## How to set up the DRVEGRD 152

1. Make sure that the prerequisites are available.
2. Run the DriveRecorder
3. Load the .dsk file (File -> Load Desktop)
4. Load the .csdx file (File -> Load CanSpec)
5. Configure the DRVEGRD 152

## How to configure the DRVEGRD 152

The DriveRecorder software offers the possibility to configure the DRVEGRD 152. The following configuration is just an example of how the sensor can be set. To configure the DRVEGRD 152, you must switch to the Commad Configurator tab. Each command must be sent separately. Note that the parameter detection\_sensitivity is a custom user command.

<table><thead><tr><th width="318">parameter</th><th>value</th><th>description</th></tr></thead><tbody><tr><td>ip_source_address</td><td>ip address in decimal form</td><td>IP address of the sensor</td></tr><tr><td>ip_dest_address</td><td>ip address in decimal form</td><td>IP address where data should be sent to</td></tr><tr><td>ip_dest_port</td><td>55555</td><td>UDP port used for sending data</td></tr><tr><td>output_control_target_list_can</td><td>0</td><td>Disable output of target list via CAN</td></tr><tr><td>output_control_target_list_eth</td><td>1</td><td>Enable output of target list via ETH</td></tr><tr><td>frequency_sweek_idx</td><td>0</td><td>Enable medium range operation</td></tr><tr><td>detection_sensitivity</td><td>2</td><td>Sensor detection sensitivity: high</td></tr><tr><td>comp_eeprom_ctrl_save_param_sec</td><td>2010</td><td>Saving parameters to EEPROM</td></tr></tbody></table>

## DRVEGRD data in ROS2

smartmicro provides a node (see prerequisites) that interfaces with the smartmicro radar driver and publishes the data acquired by the sensor via the ROS2 pipeline.

1. clone the repository from GitHub

```
git clone https://github.com/smartmicro/smartmicro_ros2_radars.git
```

2. change the folder to the cloned repository

```
cd smartmicro_ros2_radars
```

3. replace "lib-linux-x86\_64\_gcc\_9" with "lib-linux-armv8-gcc\_9". Save and exit the file with **Ctrl+X**

```
nano umrr_ros2_driver/CMakeLists.txt
```

4. customize the configuration file. Save and exit the file with **Ctrl+X**

```
nano umrr_ros2_driver/param/radar.params.template.yaml
```

```yaml
# a small example
/smart_radar:
  ros__parameters:
    adapters:
      adapter_0:
        hw_dev_id: 3
        hw_iface_name: eth1
        hw_type: eth
        port: 55555
    master_data_serial_type: port_based
    master_inst_serial_type: port_based
    sensors:
      sensor_0:
        link_type: "eth"
        model: "umrr9d_v1_0_3"
        dev_id: 3
        id: 100
        ip: "10.0.0.21"
        port: 55555
        frame_id: "umrr"
        history_size: 10
        inst_type: "port_based"
        data_type: "port_based"
        uifname: "umrr9d_t152_automotive"
        uifmajorv: 1
        uifminorv: 0
        uifpatchv: 3
        
    
```

5. give smart\_extract.sh the rights to execute

```
chmod +x smart_extract.sh
```

6. get the Smart Access release

```
./smart_extract.sh
```

7. build the package

```
colcon build
```

7. setup the environment

```
source install/setup.bash
```

7. launch the node. Note that the **&** ensures that the command is executed in the background.

```
ros2 launch umrr_ros2_driver radar.launch.py&
```

8. Display the data to validate whether the node is running.

```
ros2 topic echo /smart_radar/targets_0
```
