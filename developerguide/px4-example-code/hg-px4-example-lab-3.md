---
description: Compiling our new example code into PX4
---

# HG-PX4 Example Lab 3: Building Code

## Building our code to run on the FMU

Now that we have prepared two applications for use on our drone, we want to run them in order to confirm that they work. 

We can test and debug code like this in a few different ways: 

* using SITL \(software in the loop\) in a simulation environment like Gazebo or AirSim. The code is running on a simulated flight controller. Fast to iterate and test unusual conditions in a safe way. Only the simulated hardware crashes, not a real drone! Sometimes not representative of real-world environment however. 
* using HITL \(hardware in the loop\) where the code is actually running on target hardware, but all the sensor and IO is attached to the simulation environment. It is more complicated to configure than SITL, but can expose things like processor or system hardware limitations or bottlenecks. 
* on the actual hardware, which is closest to reality, but slower and more dangerous to fully test.

When testing code for complex systems like drones, SITL is good practice because you can make sure it works properly and look for failure conditions in advance of loading it on a real physcial drone. This helps prevent accidents! However since we're just reading sensor measurements and publishing LED commands, we can't really harm our drone, so we're going to go the "real hardware" route. This will also give you experience in loading code to the FMU.

### Adding our code to the local PX4 project

In order to build our code in PX4, we place the code in the correct location with the necessary supporting files. Lets take the `hg_led` example from Lab 2.  Save the source code you wrote to a file named `hg_led.c` as seen here:

![](../../.gitbook/assets/image%20%28174%29.png)

#### CMakeLists.txt

Now place this file into a _folder_ also named `hg_led`. Your folder name should usually match your main file's name. Next create a text file called `CMakeLists.txt` that will tell `cmake` how to build our application. Inside our `CMakeLists.txt` file, add the following code:

```text
px4_add_module(
	MODULE examples__hg_led
	MAIN hg_led
	STACK_MAIN 2000
	SRCS
		hg_led.c
	DEPENDS
	)
```

Lets explain what's going on here:

* `px4_add_module()`: This tells `cmake` that we are adding a new module \(or application\) to the firmware.
* `MODULE`: `examples__hg_led` tells `cmake` that this application is located in the `Firmware/src/examples` folder. If you add an application to another source folder, you essentially write `<folder_name>__<app_name>`. 
* `MAIN`: This tells `cmake` what the main function name is. This is your application name. In this case, it's `hg_led`.
* `SRCS`: Add the names of your source files under this parameter.
* `DEPENDS`: If your application depends on another application, add them here. Since our application is an independent program there are no other file dependencies listed here.

Now that we have our `CMakeLists.txt` file configured, we also have to tell PX4 to build it for our board. First, we need to move or copy our `hg_led` folder containing the source files and the `CMakeLists.txt` that we created into the `Firmware/src/examples/` directory.   
It should look like this:

![](../../.gitbook/assets/image%20%28164%29.png)

Navigate to `Firmware/boards/nxp/fmuk66-v3/default.cmake` and add `hg_led` to the list under `EXAMPLES`.  All of these examples listed here will be built into your PX4 image and will be able to be called from the command line on the FMU when running!   
Your `EXAMPLES` parameter should now look something like this: 

```text
	EXAMPLES
		fixedwing_control # Tutorial code from https://px4.io/dev/example_fixedwing_control
		hello
		hg_led # Our example application!
		hwtest # Hardware test
		#matlab_csv_serial
		px4_mavlink_debug # Tutorial code from http://dev.px4.io/en/debug/debug_values.html
		px4_simple_app # Tutorial code from http://dev.px4.io/en/apps/hello_sky.html
		rover_steering_control # Rover example app
		uuv_example_app
		work_item
```

### Building PX4 and flashing the board

Now that we've added our new application to PX4, let's build our new firmware by running this command in our terminal: make nxp\_fmuk66-v3

![](../../.gitbook/assets/image%20%28168%29.png)

{% hint style="success" %}
If you were targeting another board, for example the `UCANS32K146`, you would just substitute that board name instead of `nxp_fmuk66-v3`.   
  
Hint: Since the command line supports "tab completion". if you type part of the name and press tab, the valid and correct board options will then show. 
{% endhint %}

After entering the make command, the software will start building. Assuming no errors or failures, you should see an output similar to this once it's done. \(If there is a failure, read the output carefully, often it is something simple that needs correction like a missing ";" at the end of a line of C code.\):

![](../../.gitbook/assets/image%20%28175%29.png)

Now, you can navigate to `/Firmware/build/nxp_fmuk66-v3_default/` to find your **\*.px4** file which you can flash to your RDDRONE-FMUK66 using QGroundControl! \(or a .bin file via the Segger JLINK SWD debugger tools.\)

