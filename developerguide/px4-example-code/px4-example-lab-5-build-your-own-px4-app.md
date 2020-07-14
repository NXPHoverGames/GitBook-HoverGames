# PX4 Example Lab 5 \(Build your own PX4 app\)

You've made it to the last example lab on this gitbook! In this lab, we will learn how to create our own app that harnesses both the publish and subscribe protocols in uORB.

## Objective

In this lab, we won't be guiding you through creating this program, but we will give instructions on how to complete it. Don't worry though, if you get stuck, there's a solution file that you can reference to learn how to complete this lab.

The objective of this lab is to harness the data published by the magnetometer \(compass\) on the FMU and control the RGB LED when you're facing north. You should also print to the Mavlink console that you're facing north along with the magnetometer data.

## Tips

If you get stuck, here are some tips to help you out:

* The two uORB topics that you'll want to use are
  * `vehicle_local_posititon`
  * `led_control`
* The `yaw` value in `vehicle_local_position` is in radians. You can use this data in radians, or you may convert to degrees if you'd like.
* The `yaw` value in degrees for North is `350 < degrees < 10`. When the degrees hit 359, they wrap back to 0.

## Demo

Here's a small demo of what the output should look like. You should have some sort of logging in the Mavlink console as well as the LED flashing when you're facing north.

![](../../.gitbook/assets/part1.gif)

## Solution

If you need the solution to figure it out, or want to view some of the other tutorial files, go to this link: [https://github.com/NXPHoverGames/Tutorials/blob/master/TutorialApplications/hg\_magnet/hg\_magnet.cpp](https://github.com/NXPHoverGames/Tutorials/blob/master/TutorialApplications/hg_magnet/hg_magnet.cpp)

## Extra Credit!

If you'd like, you could make the LED blink a different color for North, South, East, and West!

