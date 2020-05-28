---
description: Instructions for building the bootloader from source using the console.
---

# Building the bootloader

## Pre-built bootloader binary

It is not \(always\) required to build the bootloader youself. We provide a pre-built bootloader binary on the Downloads page:

{% page-ref page="../downloads.md" %}

## Building the PX4 bootloader from source

To build the bootloader, you will need the [PX4 development toolchain](tools/px4-toolchain.md), which you should have setup in your development virtual machine. When the toolchain has been installed, you can run the following commands in the command line tool available on your operating system or installed through the development toolchain.

* First, clone the PX4 bootloader repository: `git clone https://github.com/PX4/Bootloader`
* Then, change your working directory to the just cloned repository: `cd Bootloader/`
* Synchronize submodules: `git submodule sync --recursive`
* Update the submodules:`git submodule update --recursive --init`
* Build the RDDRONE-FMUK66 PX4 bootloader: `make fmuk66v3_bl`

The bootloader is now available under `Bootloader/build/fmuk66v3_bl/fmuk66v3_bl.bin`

## Updating your local clone of the PX4 Bootloader repository

In case you already have the bootloader repository cloned, you can pull in the most recent changes and rebuild the bootloader binary. Open a console and go to your local clone of the PX4 Bootloader repository

If you want to checkout another branch, or switch back to master branch, you can do that first.

* Fetch available branches in the remote \(online\) repository: `git fetch`
* Checkout another branch: `git checkout branchname`

Now make sure your local repository is up-to-date with the latest upstream changes:

* Pull in new changes: `git pull`
* Synchronize submodules: `git submodule sync --recursive`
* Update the submodules:`git submodule update --recursive --init`

You can now rebuild the RDDRONE-FMUK66 PX4 bootloader: `make fmuk66v3_bl`

## Writing the bootloader

Instructions for [writing the bootloader to the board](../userguide/programming.md#writing-the-bootloader-to-the-board) are availabe in the user guide. [More detailed instructions](program-software-using-debugger.md) for programming binaries onto the FMU are available in the developer guide.

