---
description: Instructions on how to build the PX4 firmware from source using the console.
---

# Building PX4 firmware

Most of the times when using the RDDRONE-FMUK66 (NXPhlite) flight controller, you will only be using the latest stable firmware, which can be directly installed using QGroundControl&#x20;

[https://docs.px4.io/main/en/config/firmware.html](https://docs.px4.io/main/en/config/firmware.html)\


{% embed url="https://docs.px4.io/main/en/config/firmware.html" %}

However, some times you want to be able to test the latest development version, or your own modifications. To do this, you can build the latest version yourself, and load it on the FMU. On this page you will find the steps on how to approach this.

## Building the firmware

When you have your [toolchain set up](tools/toolchain-installation.md), you can start building firmware. As part of the installation, the firmware has already been cloned to your computer under the folder `~/src/Firmware`. To build the firmware for RDDRONE-FMUK66 (NXPhlite), open a terminal in this folder (On Windows, follow steps 1. and 2. at \
[https://dev.px4.io/main/en/setup/dev\_env\_windows\_cygwin.html#getting\_started](https://dev.px4.io/main/en/setup/dev\_env\_windows\_cygwin.html#getting\_started)

{% embed url="https://dev.px4.io/main/en/setup/dev_env_windows_cygwin.html#getting_started" %}

and use the following command:

```
make nxp_fmuk66-v3_default
```

This will create a firmware file called `nxp_fmuk66-v3_default.px4`, which can be found at `~/src/Firmware/build/nxp_fmuk66-v3_default`. This is the firmware file based on the current master, which can already by uploaded to the RDDRONE-FMUK66 using QGroundControl. It will also create a `nxp_fmuk66-v3.bin` file in the same location which you can program with the debugger.

You can also have the building process directly upload the firmware to the FMU. To do this, run the following command:

```
make nxp_fmuk66-v3_default upload
```

This will also build the current version of the firmware, but when it is finished building it will also upload the firmware to a connected RDDRONE-FMUK66. If you do not have an FMU connected or the uploader does not recognize a connected FMU, it will display a message that it is waiting for a "BootLoader". If you have not connected the FMU yet, the uploading will commence whenever you plug it in. If the FMU is already connected, you can try resetting the FMU using the reset button on the side.

### Building different branches

If you want to test an experimental branch to test an experimental feature or fix, you can simply checkout the different branch, because the firmware folder is a clone of the Git repository.

```bash
git fetch
git checkout branch_name
```

The project contains a lot of submodules, of which different versions are being used between different branches and commits of the firmware project. Therefore it is recommended to update them every time you switch between branches. You can use the following sequence of commands to update all the submodules after a checkout:

```bash
git submodule sync --recursive
git submodule update --recursive --init
make distclean
```

### Update your local clone of the PX4 Firmware repository

You can pull in the latest changes from the remote repository using the following command:

```bash
git pull
```

This is useful if you already have a local clone of the repository and you want to get the latest version of the code. Using this, you don't have to clone the repository again.
