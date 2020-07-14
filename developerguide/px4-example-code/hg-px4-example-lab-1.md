---
description: uORB messaging protocol
---

# HG-PX4 Example Lab 1: uORB Subscribe

In this section, we will go through some of the PX4 example code and explain how it works, and then write our own PX4 app to run on the RDDRONE-FMUK66. As a prerequisite, you should download the PX4 examples outlined in the [previous section](./), and then come back to this section. 

## Getting Started

Lets review uORB, a messaging protocol that will be used in many of the examples.

### uORB

uORB is a publish/subscribe messaging protocol that is deeply embedded in the PX4 system. Now, you may ask, what is a publish/subscribe messaging protocol? Lets find out!

#### Publish/Subscribe messaging protocols

![Example of publishers and subscribers in PX4 examples](../../.gitbook/assets/image%20%28163%29.png)

In the image above, you can see that PX4 is a publisher of a multitude of different "topics". These topics are similar to a "struct" in C. They have a name \(such as led\_control\) and can contain different variables that correspond to that topic. 

For example the topic "sensor\_gyro" contains the following information:

```text
LINK to file: https://github.com/PX4/Firmware/blob/master/msg/sensor_gyro.msg
-----------------------------------------------------------------------------

uint64 timestamp # time since system start (microseconds)
uint64 timestamp_sample

uint32 device_id # unique device ID for the sensor that does not change between power cycles

float32 x # angular velocity in the NED X board axis in rad/s
float32 y # angular velocity in the NED Y board axis in rad/s
float32 z # angular velocity in the NED Z board axis in rad/s

float32 temperature # temperature in degrees celsius

uint32 error_count
uint8 ORB_QUEUE_LENGTH = 8
```

The **sensor\_gyro** topic contains quite a few variables. Each topic is able to be sent as a **message** from a publisher to a subscriber. A timestamp is included each message, and that is defined in the .msg file. 

The primary data of interest is for this topic is x, y, z, and temperature variables. The gyro on the RDDRONE-FMUK66 outputs angular velocities in the x, y, and z directions, and also reports the temperature. 

Again in the image above, it shows that **hg\_gyro** subscribes to the **sensor\_gyro** topic to harness the data published to it. 

## HG\_Gyro Subscriber Example 

Above we've shown the **sensor\_gyro** uORB message, lets go through the HoverGames **HG\_gyro** example code and find out how we can print gyro measurements to the MavLink console.

#### License 

First, we have to include the header license comment since the software is permissively licensed:

```text
/****************************************************************************
 *
 *   Copyright (c) 2012-2016 PX4 Development Team. All rights reserved.
 *   Copyright 2019 NXP.
 *
 * Redistribution and use in source and binary forms, with or without
 * modification, are permitted provided that the following conditions
 * are met:
 *
 * 1. Redistributions of source code must retain the above copyright
 *    notice, this list of conditions and the following disclaimer.
 * 2. Redistributions in binary form must reproduce the above copyright
 *    notice, this list of conditions and the following disclaimer in
 *    the documentation and/or other materials provided with the
 *    distribution.
 * 3. Neither the name of the copyright holder nor the names of its 
 *    contributors may be used to endorse or promote products derived 
 *    from this software without specific prior written permission.
 *
 * THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
 * "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
 * LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
 * FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE
 * COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
 * INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
 * BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS
 * OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED
 * AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
 * LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN
 * ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
 * POSSIBILITY OF SUCH DAMAGE.
 *
 ****************************************************************************/

/**
 * @file hg_gyro.c
 * Minimal application reading gyro values from uORB service
 *
 * @author Leutrim Mustafa
 */
```

Alright, with that out of the way, let's start!

### Headers

We will review each section of code and then combine everything into one file at the end. The first section of code is where we include all of the necessary header \(\*.h\) files we will need for this example. 

```text
// px4_config and posix are needed for just about every PX4 user application.
#include <px4_platform_common/px4_config.h>
#include <px4_platform_common/posix.h>

// These are basic headers that will be needed for polling messages,
// manipulting strings, standart input/output, and POSIX compliance.
#include <unistd.h>
#include <stdio.h>
#include <poll.h>
#include <string.h>

// These headers are for the uORB messaging system. We include the base uORB
// header and a header for the topic we will be using (sensor_gyro!)
#include <uORB/uORB.h>
#include <uORB/topics/sensor_gyro.h>
```

### Main Function Declaration

Now that we have all of our headers included in our application, we can begin the real stuff. We define our main function and export it so that other applications can call upon it in PX4.

```text
// Export main function so that we can call on it in PX4
__EXPORT int hg_gyro_main(int argc, char *argv[]);

// Define our main function
int hg_gyro_main(int argc, char *argv[]) {

    PX4_INFO("Hello Hovergames gyro!"); // Prints "Hello Hovergames Gyro!" to the console
```

When creating our own PX4 user apps, it's necessary to name your main function  **`<filename>_main`** so that PX4 can tell what the new function is named and how to call it. 

The **`int argc, char *argv[]`**arguments in the main function allow the addition of command line parameters to your app when you call it from the PX4 MavLink console or in a script. While they aren't necessary for this example, it doesn't hurt to include them for future iterations of our app!

### Subscribing to the sensor\_gyro topic

Next, we will go through the code to print out our gyro measurements. We need to set up the uORB messaging protocol to _subscribe_ to the **sensor\_gyro** topic:

```text
    // Subscirbe to "sensor_gyro", then set a polling interval of 200ms
    int gyro_sub = orb_subscribe(ORB_ID(sensor_gyro));
    orb_set_interval(gyro_sub, 200);
    
    // Configure a POSIX POLLIN system to sleep the current thread until
    // data appears on the topic
    px4_pollfd_struct_t fds_gyro;
    fds_gyro.fd = gyro_sub;
    fds_gyro.events = POLLIN;
```

After subscribing to the "**sensor\_gyro**" topic and limit the update rate \(interval\) to 200ms, we set up a polling structure which allows the application to enter sleep mode until another set of data gets published to the topic. This makes our application efficient and prevents it from eating CPU cycles when waiting for new data!

### Setup for the for loop

Using a simple integer counter variable in a loop allows the program to end after a specified number of times. We will print out a text chart so that we can visualize the data a little bit easier. 

```text
    int counter = 20;
    printf("%02i | gyro_x | gyro_y | gyro_z\n", counter);
    printf("-----------------------------------\n");
```

### Fetching data from the topic

That was easy enough, now lets create our for loop and actually start grabbing data from the "sensor\_gyro" topic.

```text
    // Loop a specified number of times
    for(int i = 1; i <= counter; i++) 
    {
        // Allow the POSIX POLLIN system to poll for data, with 1000ms timeout
        int poll_ret = px4_poll(&fds_gyro, 1, 1000);
        
        // If px4_poll returns 0, then the poll system timed out! Throw an error.
        if(poll_ret == 0) 
        {
            PX4_ERR("Got no data within a second");    
        } 
        
        // If it didn't return 0, we got data!
        else 
        {
            // Double check that the data we recieved was in the right format (I think - need to check)
            if(fds_gyro.revents & POLLIN) 
            {
            
                // Create a sensor_gyro_s struct to store the data we recieved
                struct sensor_gyro_s gyro;
                
                // Copy the data over to the struct
                orb_copy(ORB_ID(sensor_gyro), gyro_sub, &gyro);
                
                // Finally, print the data!
                printf("printf("%02i |  %+2.2f  |  %+2.2f  |  %+2.2f  \n", i, 
                    (double)gyro.x, (double)gyro.y, (double)gyro.z);
            }
        }
    }
    
    // Tell the user that the application is ending...
    PX4_INFO("Hovergames gyro exit");
    
    // Typical C exit :)
    return 0;
    
}
```

This section of code is polling the **sensor\_gyro** uORB topic and then copying the data to a structure that allows us to print it out on the MavLink console. If the poll doesn't receive data within 1 second, it will timeout and we will send an error message.

There we have it! We have just written our first example program for the FMU RDDRONE-FMUK66 running PX4 flight stack on NuttX RTOS. 

In the next lab we will look at _publishing_ to a uORB topic to control the RGB LED on the FMU.

