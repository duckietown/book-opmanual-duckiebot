
# Flashing Instructions for the OKDO Jetson Nano C100

## Overview

The instructions below have been tested with JP4.6.6 with the Duckiebot image `v1.4.6`. Following this guide, the root partition from the eMMC will now point to the SD card while all other partitions remain on the eMMC.

The reason for this modification is that the C100 uses the production version of the NVIDIA Jetson Nano module, which uses eMMC instead of an SD card interface. We need to make some small changes to use pre-built SD card images.

## Prerequisites

- Host computer running Linux (Ubuntu 18.04 or newer recommended)
- Docker installed on the host
- Power supply for the Jetson Nano
- USB cable (micro USB to connect to the C100)
- Display, keyboard, mouse, and Ethernet cable for initial setup

## Step A: Flash the C100 using Dockerized Jetson Flasher

Instead of using NVIDIA SDK Manager, we'll use the dockerized Jetson flasher for a more streamlined experience:

1. **Clone the flasher repository:**

   ```bash
   git clone https://github.com/duckietown/dt-jetson-nano-flasher
   cd dt-jetson-nano-flasher
   ```

2. **Download the Linux4Tegra BSP and image:**

   ```bash
   mkdir -p ~/Nvidia && cd ~/Nvidia
   wget https://developer.nvidia.com/downloads/embedded/l4t/r32_release_v7.6/t210/jetson-210_linux_r32.7.6_aarch64.tbz2
   wget https://developer.nvidia.com/downloads/embedded/l4t/r32_release_v7.6/t210/tegra_linux_sample-root-filesystem_r32.7.6_aarch64.tbz2
   ```

3. **Build the Docker image:**

   ```bash
   cd dt-jetson-nano-flasher
   docker-compose build
   ```

4. **Put the Jetson Nano into recovery mode:**
   - Power off the Jetson Nano
   - Short the `FC REC` and `GND` pins with a jumper
   - Power on the Jetson Nano
   - Connect the micro USB cable from your host to the C100
   - Verify the device is in recovery mode: `lsusb | grep NVIDIA` (should show "NVIDIA Corp. APX")

5. **Run the flashing container:**

   ```bash
   docker-compose run --rm ubuntu
   ```

6. **Inside the container, prepare and flash:**

   ```bash
   # Extract the BSP
   cd /Nvidia
   tar xf jetson-210_linux_r32.7.6_aarch64.tbz2
   cd Linux_for_Tegra/rootfs
   tar xf /Nvidia/tegra_linux_sample-root-filesystem_r32.7.6_aarch64.tbz2
   cd ..
   
   # Apply binaries
   sudo ./apply_binaries.sh
   
   # Flash the device (use jetson-nano-emmc for production modules)
   sudo ./flash.sh jetson-nano-emmc mmcblk0p1
   ```

   The flashing process will take several minutes. Once complete, the Nano will reboot into Ubuntu.

## Step B: Boot to Desktop

Unplug the C100 from the host and connect a display, keyboard, mouse, and Ethernet cable.
Make sure to **remove the jumper** shorting the `FC REC` and `GND` pins.
Power up the device and follow the onscreen setup guide until you reach the desktop.

## Step C: Configure SD Card Interface and Root Path

Perform the following steps on the Jetson Nano C100 (all commands are executed in the shell). Total time: approximately 15 minutes.

### Enable SD Card Interface

First, we need to enable the SD card interface using the following commands:

1. **Clone the device tree overlays repository:**

   ```bash
   git clone https://github.com/Seeed-Studio/seeed-linux-dtoverlays.git
   ```

2. **Configure and build the overlay:**

   ```bash
   cd seeed-linux-dtoverlays
   sed -i '17s#JETSON_COMPATIBLE#\"nvidia,p3449-0000-b00+p3448-0002-b00\"\,\"nvidia\,jetson-nano\"\, \"nvidia\,tegra210\"#' overlays/jetsonnano/jetson-sdmmc-overlay.dts
   make overlays/jetsonnano/jetson-sdmmc-overlay.dtbo
   sudo cp overlays/jetsonnano/jetson-sdmmc-overlay.dtbo /boot/
   ```

3. **Configure the hardware module:**

   ```bash
   cd /boot/
   sudo /opt/nvidia/jetson-io/config-by-hardware.py -l
   ```

   This should display a list of hardware modules. Verify that `reComputer sdmmc` is present in the list.

4. **Enable the SD card module:**

   ```bash
   sudo /opt/nvidia/jetson-io/config-by-hardware.py -n "reComputer sdmmc"
   ```

5. **Reboot the system:**

   ```bash
   sudo reboot
   ```

### Modify Root Path Configuration

After rebooting, we need to modify the root path to point to the SD card:

1. **Edit the extlinux configuration file:**

   ```bash
   sudo nano /boot/extlinux/extlinux.conf
   ```

   Find all lines containing `root=/dev/mmcblk0p1` and change them to `root=/dev/mmcblk1p1`.

   Save the file and exit the editor.

## Step D: Use SD Card with Duckiebot Image

Now you can insert your SD card flashed with the Duckiebot image and use it normally.

For detailed instructions on setting up your Duckiebot, refer to the [Duckiebot operation manual](https://docs.duckietown.com/daffy/opmanual-duckiebot/intro.html).  
