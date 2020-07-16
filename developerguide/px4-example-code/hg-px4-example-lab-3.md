# HG-PX4 Example Lab 3: Building Code

## Building our code to run on the FMU

Now that we have built two applications for use on our drone, we need to run them to confirm that they work. We could do this in one of two ways: using SITL \(software in the loop\) or on HITL \(hardware in the loop\). When testing code, using SITL is good practice because you can make sure it works before uploading it to your hardware in case it fails. Since we're just reading sensor measurements and publishing LED commands, we can't really harm our drone, so we're going to go the hardware route.

### Adding our code to the project

In order to build our code into the PX4 system, we must place the code in the correct place with the necessary files. In this example, we are just going to use the hg\_led example from lab 2. Take your source code that you wrote and save it to a file named `hg_led.c` as seen here:

![](../../.gitbook/assets/image%20%28174%29.png)

Place this file into a folder named `hg_led`. Your folder name should always match your main file's name. Now that we have that done, we must create a `CMakeLists.txt` file that tells `cmake` how to build our application. Inside our `CMakeLists.txt` file, add the following code:

```text
px4_add_module(
	MODULE examples__hg_led
	MAIN hg_led
	STACK_MAIN 2000
	SRCS
		hg_gyro.c
	DEPENDS
	)
```

Lets explain what's going on here:

* `px4_add_module()`: This tells `cmake` that we are adding a new module \(or application\) to the firmware.
* `MODULE`: `examples__hg_led` tells `cmake` that this application is located in the `Firmware/src/examples` folder. If you add an application to another source folder, you essentially write `<folder_name>__<app_name>`. 
* `MAIN`: This tells `cmake` what the main function name is. Just make this your application name. In this case, it's `hg_led`.
* `SRCS`: Add the names of your source files under this parameter.
* `DEPENDS`: If your application depends on another application, add them here. Since our application is an independent program, it don't depend on nobody. :\) \(take this out for official lab manual haha\)

Now that we have our `CMakeLists.txt` file configured, we have to tell PX4 to build it for our board. First, we need to place our `hg_led` folder that we created in the `Firmware/src/examples/` directory. It should look like this:

![](../../.gitbook/assets/image%20%28164%29.png)

Next, navigate to `Firmware/boards/nxp/fmuk66-v3/default.cmake` and add `hg_led` to the list under `EXAMPLES`. Your `EXAMPLES` parameter should now look like this: 

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

Great! We've successfully added our new application to PX4. Now, let's build our new firmware by running this command in our terminal:

![](../../.gitbook/assets/image%20%28168%29.png)

You should see an output similar to this once it's done:

![](../../.gitbook/assets/image%20%28175%29.png)

Now, you can navigate to `/Firmware/build/nxp_fmuk66-v3_defualt/` to find your \*.px4 file which you can flash to your RDDRONE-FMUK66 using QGroundControl!

