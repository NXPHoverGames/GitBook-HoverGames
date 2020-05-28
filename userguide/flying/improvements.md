---
description: Some options to improve the flight characteristics of your drone.
---

# Improving flight

## Practice makes perfect

As is often the case, practice makes perfect. When you are flying a drone for the first time, it's not going to be easy and you will make mistakes. As you grow more confident and get more familiar with the controls and the different flight modes, you will be able to fly quicker and more aggressive.

## PID tuning

While the default values should be a good starting point, the controllers that are part of PX4 are not perfectly tuned for every drone. Some improvements are always possible, but are probably not needed unless you are using the drone in more extreme situations, or when you are doing more advanced flying.

The default PID values for the S500 airframe preset are listed below:

```text
MC_ROLL_P 6.5
MC_ROLLRATE_P 0.18
MC_ROLLRATE_I 0.15
MC_ROLLRATE_D 0.003
MC_PITCH_P 6.5
MC_PITCHRATE_P 0.18
MC_PITCHRATE_I 0.15
MC_PITCHRATE_D 0.003
```

The PX4 user documentation has a multicopter tuning guide that will be useful if you decide to do your own PID tuning.

{% embed url="http://docs.px4.io/en/config\_mc/pid\_tuning\_guide\_multicopter.html" %}

## Use GPS as primary altitude source

You may want to try using GPS as the primary altitude source instead of the barometer \(pressure sensor\). The result is still fused between the two. Depending on your GPS accuracy it might improve the altitude control of your drone. To set GPS as the primary altitude source, set parameter EKF2\_HGT\_MODE to GPS.

{% embed url="https://dev.px4.io/en/advanced/parameter\_reference.html\#ekf2" %}

