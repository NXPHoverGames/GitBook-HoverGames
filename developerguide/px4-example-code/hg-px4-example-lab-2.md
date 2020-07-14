# HG-PX4 Example Lab 2 \(uORB Publish\)

In the last lab, we learned what uORB and publish/subscribe protocols were. Then, we wrote a bit of code that allowed us to print out some gyro measurements to the MavLink console! The program we wrote was only half of the equation, though, as we only used the "subscribe" portion of uORB. In this lab, we will publish some data to a topic that will control the RGB LED on the RDDRONE-FMUK66. The topic we are publishing to is subscribed to by an internal PX4 program that handles LED control.

## HG\_led

To start, let's get the license for this source code out of the way:

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
 * @file hg_led.c
 * Minimal application for led control
 *
 * @author Leutrim Mustafa
 */
```

### Includes

As in the last lab, we will go ahead and include our headers to the source code. The headers will be nearly the same, except we will be changing the uORB topic from `sensor_gyro` to `led_control`.

```text
#include <px4_platform_common/px4_config.h>
#include <px4_platform_common/posix.h>
#include <unistd.h>
#include <stdio.h>
#include <poll.h>
#include <string.h>

#include <uORB/uORB.h>               // asynchronous messaging API used for inter-thread/inter-process communication
#include <uORB/topics/led_control.h> // uORB for led_control
```

### Main function

Next we will create our main function and export it, much like the last lab. 

```text
__EXPORT int hg_led_main(int argc, char *argv[]); // Export main for starting in another thread

int hg_led_main(int argc, char *argv[])
{
    PX4_INFO("Hello Hovergames LED");
```

First, we exported our hg\_led\_main function. Remember, your main function should be called `<filename>_main`. Then, we added in a `PX4_INFO()` function to show that the program has started. 

### Setup

We will create a structure that we can save LED data to. This structure will be used to publish the data to the `led_control` uORB topic.

```text
    // Create structure to store data in
    struct led_control_s led_control;

    // Clear the structure by filling it with 0s in memory
    memset(&led_control, 0, sizeof(led_control));

    // Create a uORB topic advertisement
    orb_advert_t led_control_pub = orb_advertise(ORB_ID(led_control), &led_control);
```

The first step is to create the structure itself. Here, we created an led\_control\_s structure and named it led\_control. Then, we called `memset()` and filled the structure we created with zeros. We do this because the memory we allocate could have bogus data in it, and in a safety critical platform such as a drone, we don't want to send bogus data if our data allocation code fails. After, we create a uORB topic advertisement variable that allows us to publish to the `led_control` topic.

### Setting LED control data

Once we have done our initial setup, we can start filling our `led_control` structure with data. 

{% hint style="info" %}
The led\_control uORB message definition can be found [here](https://github.com/PX4/Firmware/blob/master/msg/led_control.msg). This file outlines all of the different parameters than can be set for led\_control.
{% endhint %}

Colors, modes, and priorities can be set using the parameters seen in the link above. In this example, we are going to tell the LED to blink 10 times at max priority with the color green.   
Here's how to do that:

```text
    led_control.num_blinks = 10; // Blink 10 times
    led_control.priority = LED_CONTROL_MAX_PRIORITY; // Set our app to max priority
    led_control.mode = LED_CONTROL_MODE_BLINK_NORMAL; // Set the LED mode to blink
    led_control.led_mask = 0xff; // Select all LEDs
    led_control.color = LED_CONTROL_COLOR_GREEN; // Set color to green
```

All of these parameters are easily set by defining which parameter we would like to set and then giving it a value. 

* `num_blinks` : We simply set the number of blinks to 10. You can make this whatever size you want, but don't make it too large, or your LED will blink for a very long time!,  \(\).
* `priority` : Make our LED app max priority so that something else can't override it by setting `LED_CONTROL_MAX_PRIORITY` 
  * in practice, max priority is reserved for things like error LED sequences.
* `mode` : We set the mode to `LED_CONTROL_MODE_BLINK_NORMAL` for a normal blink sequence. 
* `led_mask` : We set this to `0xff` which tells the led controller to blink all LEDs.
* `color` : Set to `LED_CONTROL_COLOR_GREEN` ! If you'd like to set it to a different color, feel free!

### Publishing our LED data

In order to tell the LED controller to use the parameters we set, we have to send a uORB message with the structure we created. We will use the `orb_publish()` function to do so:

```text
    orb_publish(ORB_ID(led_control), led_control_pub, &led_control);
```

And there we have it! Once this command is run, the uORB message with our data will be sent, and our LEDs will start blinking green.   
  
To close out the program, let's print something to the MavLink console that shows our program is done running.

```text
    PX4_INFO("Hovergames LED exit");
    
    return 0; // return of main function
    
}
```

### Conclusion

We have now learned how to both subscribe and publish uORB messages in PX4. Next, we will create our own program that uses our newfound knowledge to manipulate the LED on the RDDRONE-FMUK66. 

