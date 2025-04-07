```{seo}
:description: How to reflash a Jetson Nano 4GB development kit.
:keywords: Duckietown, Duckiebot, Nvidia Jetson Nano, Jetson Nano, Jetson Nano development kit, Jetson does not boot, white screen nvidia logo, jetson nano 4gb reboots continuously
```

(reflash-jetson-4gb)=
# Debug - How to (re)flash the NVIDIA Jetson Nano 4GB developer kit

```{needget}
* A NVIDIA Jetson Nano 4GB development kit with onboard `eMMC` memory (hereafter, the "Jetson")
* One computer (the "base station") with roughly 50GB of free hard drive space
* Base station with native Ubuntu installation (tested on 18.04, 22.04, 24.04)
* Internet access to download files (not needed if files are provided in other ways)
* A power source for the Jetson Nano, e.g., 1x 5V 2A DC jack power adapter, or, 1x Duckietown HUT (3.1, 3.15) and 1x micro-USB 5V 2A power adapter
* 1x micro-USB to base station cable (with data!), or a micro-USB to USB-A adapter
* 1x jumper, or F-F Dupont cable, or stripped wire, paper clip, screwdriver (or equivalent hack to short two pins)
* (optional) 1x HDMI cable and screen
* (optional) 1x Serial cable connector to base station (to see detailed UART logs). E.g., [this model available on Amazon US][serial-cable-link] has been tested. 
* Roughly 10 minutes setup time (necessary once per base station), and 2-5 minutes per board that is (re)flashed. 

---
* A Jetson Nano 4GB development kit that boots correctly and does not get stuck on an NVIDIA logo at startup.
```

```{warning}
Do not undergo this procedue unless your Jetson is affected by the booting problem described below. This fix applies only to a very specific use case and irreversibly changes your Jetson's onboard filesystem. If you are not sure what is going on refer to the [Duckiebot FAQ Guide](troubleshooting-faq) for help with any Duckiebot setup or operation issues. 
```

(reflash-jetson-4gb-when)=
## The problem: What, when and why should I run this procedure?

* **What**: This procedure flashes the Jetson Nano Development Kit's onboard eMMC memory with a basic Ubuntu operating system (OS), necessary for the board to boot from SD card. 

* **When**: A typical example of when it is necessary to flash the Jetson is that the Duckiebot does not seem to perform the first boot, and upon connecting the Jetson Nano to a screen with an HDMI cable, you see only an NVIDIA logo (white or black backgrounds) occasionally flickering (stuck on rebooting). Upon further debugging (e.g., looking at the UART logs during boot), the Jetson seems to be recognized as a 2GB board, while it should be a 4GB board.

* **Why**: "recent" (post February 2025, to the best of our knowledge) Jetson Nano 4GB modules have a different memory module that requires a specific patch to be recognized. Without installing this patch, the onboard memory is not recognized correctly and "nothing works". Applying the patch requires (re)flashing the developer board.

```{admonition} Intersession 1 (for beginners): what are all these different flashings about?
:class: dropdown

Flashing the Jetson board is a different process than [flashing the Duckietown SD card](setup-duckiebot-sd-card), or flashing/burning an Ubuntu ISO on a thumbdrive to [install Ubuntu as an OS on the base station](system-installation). In extreme summary:
* Ubuntu installation is the OS running on your base station (laptop/desktop)
* The Jetson is a tiny but mighty computer on its own regard, and requires an OS to function. In the same way as your base station has a BIOS (that you might have accessed in the above step to, e.g., change the boot order), without installing a "basic" OS on the Jetson, it will not know where to boot from (and much more).
* Flashing the Duckietown SD card provides a more "sophisticated" OS for the Jetson, that will be used in alternative to the "basic" one installed through the procedure described below. Nonetheless, it is necessary to install the "basic" OS on the Jetson to let it know to read the SD card upon booting. 
```

```{admonition} Intersession 2 (for beginners): on Jetson Nano terminology
:class: dropdown

The terminology regarding NVIDIA Jetson Nano developer kits might be confusing, so let us clarify a few terms:

* The Jetson Nano _module_, or sometimes referred to as simply the Jetson Nano, is just the small board underneath the heat sink. These modules are all manufactured by NVIDIA, i.e., they are "original".  
* The Jetson Nano _developer board_ is the carrier board to which the Jetson Nano _module_ attaches to. This is the PCB with all the peripheral plugs (camera ports, USB ports, HDMI port, GPIO pins, etc.). These boards are no longer manufactured by NVIDIA, and a number of third-party carrier boards exist on the market.
* The combination of a Jetson Nano module and a Jetson Nano developer board is the Jetson Nano developer _kit_. In Duckietown, we sometimes lazily call "Green Jetsons" the Jetson Nano Developer Kits with _original_ developer board. Green Jetsons are such because of the color of the packaging, and are no longer on the market. We then call "Blue Jetsons" the Jetson Nano Developer Kits with _third party_ developer boards. In theory, these kits should come in blue colored packaging, but in practice they are offered by manufacturers with non-descriptive cardboard boxes. 

This said, we will just say "Jetson" or "kit" in this document, referring to the (Blue) Jetson Nano Developer Kits included in `DB21J4` Duckieboxes.
```

This procedure will not be useful to fix problems such as the Duckiebot not connecting to the network, or not moving. 

```{figure} ../_images/troubleshooting/00-white-nvidia-screen-duckiebot.jpg
:width: 30%
:name: fig:00-white-nvidia-screen-duckiebot
:alt: Duckiebot connected to a screen with flickering NVIDIA logo, failing to boot

The problem: the Duckiebot does not boot and, when connected to a screen, it shows a flickering NVIDIA logo. 
```

```{note}
In the Duckietown world, this procedure is usually performed by the Duckietown team at manufacturing stage, so users never need to worry about it. Occasionally, issues arise that slip through quality control, and it is necessary to reflash the Jetson development board to make it operational. In particular, boards received between February-April 2025 might have been affected.  
```

(reflash-jetson-4gb-how)=
## How to flash the Jetson Nano 4GB Development Kit with eMMC memory

We will have to prepare our base station, and the Jetson board before executing this procedure.

(reflash-jetson-4gb-software-step)=
### Step 1. Preparing the flashing environment on the base station

```{note}
This step needs to be executed only once, even if flashing multiple boards. 
```

#### Downloading the necessary files

   * [Jetson Nano Driver Package R32.7.6 (Jetson-210_Linux_R32.7.6_aarch64.tbz2)](https://developer.nvidia.com/downloads/embedded/l4t/r32_release_v7.6/t210/jetson-210_linux_r32.7.6_aarch64.tbz2)
   * [Sample Root Filesystem (Tegra_Linux_Sample-Root-Filesystem_R32.7.2_aarch64.tbz2)](https://developer.nvidia.com/downloads/embedded/l4t/r32_release_v7.6/t210/tegra_linux_sample-root-filesystem_r32.7.6_aarch64.tbz2)
   * [Overlay patch (overlay_32.7.5_PCN211181.tbz2)](https://drive.google.com/file/d/1Kmocz6tPmEaepPIvwKc3bT7MpJqpwkvv/view?usp=sharing)

And then create a new folder with arbitrary name (e.g., `$ mkdir jn`), and move these files in there.

#### Open a terminal window and define the following variables:

        L4T_RELEASE_PACKAGE=Jetson-210_Linux_R32.7.6_aarch64.tbz2
        SAMPLE_FS_PACKAGE=Tegra_Linux_Sample-Root-Filesystem_R32.7.6_aarch64.tbz2
        BOARD=jetson-nano-emmc

#### Extracting the flashing environment

After downloading the above files and moving them to a dedicated folder, extract the Jetson Nano driver package. This process will take a few minutes. 

    cd jn
    sudo tar xpf ${L4T_RELEASE_PACKAGE}

```{figure} ../_images/troubleshooting/reflashing-jetson-4gb-extracting-L4T.png
:width: 90%
:name: fig:reflashing-jetson-4gb-extracting-L4T
:alt: Folder structure after extracting L4T in the process of reflashing a Jetson Nano 4GB developer kit

Place the downloaded files in a dedicated folder and unzip the Jetson-210_Linux_R32.7.6_aarch64.tbz2 file.
```

#### Applying the overlay memory patch

* Stay in the `jn` folder. Unzip the previously downloaded `overlay_32.7.5_PCN211181.tbz2` file in a new folder, e.g., `/jn/overlay-temp`. 

* Open `/overlay-temp/Linux_for_Tegra/bootloader/t210ref/BCT`

* Copy the file `P3448_A00_lpddr4_204Mhz_P987.cfg` and paste it to: `/jn/Linux_for_Tegra/bootloader/t210ref/BCT/` **and overwrite the existing file**

* Open folder: `/jn/overlay-temp/Linux_for_Tegra/kernel/dtb/`

* Copy all files with `p3448` in the name (should be all files in the folder)

```{figure} ../_images/troubleshooting/reflashing-jetson-overlay-path-details.png
:width: 90%
:name: fig:reflashing-jetson-4gb-overlay-patch-details
:alt: Folder structure and files for manual overwrite of overlay patch

Copy all files of the overlay patch and replace those in the flashing environment folder.
```

* Paste all these file in `/jn/Linux_for_Tegra/kernel/dtb/` **and overwrite existing files**

#### Preparing the `rootfs` folder

Move in the `/Linux_for_Tegra/rootfs` folder, and extract the sample root filesystem:

    cd /Linux_for_Tegra/rootfs/
    sudo tar xpf ../../${SAMPLE_FS_PACKAGE}

this will take a few minutes, during which the terminal will be unresponsive. Wait patiently until the process completes. 

#### Execute the binaries and then apply the overlay patch

Move back to the `/Linux_for_Tegra` folder to apply the binaries and overlay patch:
   
    cd ..
    sudo ./apply_binaries.sh
    
once the above script is finished with installing packages, make sure you stay in the same folder and extract the overlay patch:

    sudo tar xpf ../overlay_32.7.5_PCN211181.tbz2

This process should be pretty much instantaneous.

This concludes the first step of preparing the flashing environment. We now move our attention to the Jetson Nano. 

(reflash-jetson-4gb-hardware-step)=
### Step 2. Preparing the Jetson and connecting it to the base station

To start, make sure the Jetson is powered off. If it is already assembled in your Duckiebot, remove all USB cables going into it, and all USB cables going into the HUT (detach the battery). The fan in the pictures below is unnecessary for this procedure and can be ignored.

```{figure} ../_images/troubleshooting/01-JN4GB.jpg
:width: 50%
:name: fig:01-JN4GB
:alt: A Jetson Nano 4GB with 3rd party carrier board

A Jetson Nano 4GB developer kit with 3rd party carrier board
```

#### Identify the `FC REC` pin

To (over)write the Jetson's (carrier board...) onboard memory, which in the case of this document is assumed to be a 16GB eMMC hard drive, we need to power on the Jetson while in "Forced Recovery" mode. To do so, we need to first identify the `FC REC` pin placed underneath the Jetson Nano module, near the SD card slot, as shown in {numref}`fig:02-JN-ForcedRecoveryPins`.

```{figure} ../_images/troubleshooting/02-JN-ForcedRecoveryPins.jpg
:width: 50%
:name: fig:02-JN-ForcedRecoveryPins
:alt: Jetson Nano 4GB dev kit forced recovery mode pins 

Forced recovery mode pin is labeled as `FC REC` and needs to be shorted with `GND`
```

(jetson-forced-recovery-mode)=
#### Shorting `FC REC` and `GND`

The Jetson will boot in forced recovery mode when the `FC REC` and `GND` pins are shorted when the Jetson is powered on.

```{figure} ../_images/troubleshooting/03-Shorting-for-recovery-mode.jpg
:width: 50%
:name: fig:03-Shorting-for-recovery-mode
:alt: Jetson Nano 4GB dev kit - shorting the forced recovery mode pins with a jumper cable

Short the pins, for example with a jumper or cables (neither in the Duckiebox). Any expedient to bridge those two metal pins with a conductive material (e.g., metal) will work, e.g., using the tip of a screwdriver, a paperclip, etc. Make sure to only bridge these two pins while powering the board. After the board has booted, you can safely remove the connection. 
```

#### Preparing for powering on the Jetson

These Jetsons can only be powered through the DC jack, or the `5V` and `GND` pins on the GPIO. Since DC jack cables are not included in a standard Duckiebot box, we use the available Duckietown HUT as a hack to conveniently access the GPIO power pins. 

Place your Duckietown HUT on the GPIO pins of the Jetson board. Make sure to align perfectly the Jetson's pins with the HUT's pin header, as shown in {numref}`fig:04-Adding-the-HUT-for-power` to avoid erratic behaviors. 

```{figure} ../_images/troubleshooting/04-Adding-the-HUT-for-power.jpg
:width: 50%
:name: fig:04-Adding-the-HUT-for-power
:alt: Jetson Nano 4GB dev kit - adding a Duckietown HUT for power

Connecting the Duckietown HUT to the GPIOs is a hack to power the JN without having a DC jack power cable (not included in the Duckiebox). Make sure the GPIO pins are properly aligned and not offset.
```

#### Establishing a data connection between the Jetson and the base station

Take a micro-USB to base station cable **with data channel**. Connect the micro-USB end to the Jetson Nano carrier board, as shown in {numref}`fig:05-Connect-the-JN-and-base-station`, and the other end to your base station.

```{figure} ../_images/troubleshooting/05-Connect-the-JN-and-base-station.jpg
:width: 50%
:name: fig:05-Connect-the-JN-and-base-station
:alt: Connect the Jetson Nano dev kit to the base station through the micro-USB port

Connect the Jetson Nano to the base station. Make sure the cable used carries data and not only power.
```

Unfortunately, the USB cables provided in the Duckiebox (`DB21J4`) are all power only, except for the USB-A to USB-A connection of the "Y" shaped cable, shown in {numref}`fig:the-data-cable-available-in-the-duckiebox`. If you have a USB-A to micro-USB adapter, you can use this cable. 

```{figure} ../_images/troubleshooting/the-duckiebot-Y-usb-data-cable.png
:width: 50%
:name: fig:the-data-cable-available-in-the-duckiebox
:alt: USB data cable available in the Duckiebox

This cable has data connection, but the wrong port (USB-A instead of micro-USB).
```

#### (optional) Further debugging probes

```{note}
This passage is not necessary, and can be skipped. 
```

To gain a better understanding of what will happen in the next steps, you can perform either or both of the following two steps:

1. Connect the Jetson to a screen through an HDMI cable (not shown in figure below)
2. Connect the Jetson to the base station through a serial connector ([example][serial-cable-link]). Make sure to "flip" the transmission (TXD) and receiving (RXD) channels between the connector and the Jetson. These pins on the Jetson are on the same array as the `FC REC` pin, and labeled as `UART TXD` and `UART RXD`. 


```{figure} ../_images/troubleshooting/07-optional-uart-connection.jpg
:width: 50%
:name: fig:07-optional-uart-connection
:alt: Optional UART connection through serial cable to view the detailed logs of the Jetson Nano 4GB dev kit

(optional) UART serial connection. Make sure to flip the receiving and transmission channels, i.e., connect: GND ↔︎GND, TXD ↔︎RXD, RXD ↔︎TXD
```

To visualize the UART logs on the base station, open a new terminal window and, e.g., install and run `screen`: 

    sudo apt install screen
    screen /dev/ttyUSB0 115200

Depending on the base station configuration, the number after USB could be different. Check your `/dev/tty*` after establishing the UART connection and powering the Jetson to find the right one.

#### Powering the Jetson

At this point we are ready to power up the Jetson. Connect your 5V 2A charger to the `5VRASPI` port of the HUT. You should see a (previously faint) green LED shining bright on the HUT, and a new green LED turn on on the Jetson, near the power cable. 

```{figure} ../_images/troubleshooting/06-Power-the-Jetson.jpg
:width: 50%
:name: fig:06-Power-the-Jetson
:alt: Powering the Jetson Nano 4GB dev kit through a Duckietown HUT

Power the Jetson by plugging in a 5V 2A power supply to the `5VRASPI` port of the Duckietown HUT. 
```

#### Validate the data connection

This step is critical.

**Checkpoint ✅**

Before continuing, run the following command in a terminal on your base station. 

```{testexpect}
```bash 
lsusb
---
```bash
[...]
Bus 001 Device 012: ID 0955:7f21 NVIDIA Corp. APX
[...]
```

You must see a line in the output with `NVIDIA Corp. APX`. If not, your computer and Jetson are not connected. 

```{tip}
Never skip a checkpoint!
```

Refer to the [](reflash-jetson-faq) section on this page if this checkpoint is failing.

(reflash-jetson-4gb-flashing-step)=
### Step 3. Flashing the Jetson

Continue from the base station terminal:

    sudo ./flash.sh -x 0x21 ${BOARD} mmcblk0p1

The process takes about 2-4 minutes, depending on the speed of the base station used. Successful flashing will result in:

````bash
[...]
[ 207.0591 ] Flashing completed

[ 207.0592 ] Coldbooting the device
[ 207.0622 ] tegradevflash --reboot coldboot
[ 207.0635 ] Cboot version 00.01.0000
[ 207.0673 ] 
*** The target t210ref has been flashed successfully. ***
Reset the board to boot from internal eMMC.
````


```{note}
The Jetson board will restart immediately after the process is complete. If you have an HDMI cable and screen plugged in and would like to see if the process worked, remove the short from the `FC REC` and `GND` pins while the board is being flashed (it is safe to do so).
```

**Checkpoint ✅**

If the flashing completed successfully, there are several ways to test if it worked. As long as one of these checkpoints passed, the process is completed successfully and the problem solved. 

* The easiest way: plug in a screen

```{testexpect}
Remove `FRC` jumper, data cable, and power cable from the Jetson. Plug in an HDMI cable and connect it to a screen. Plug the power cable back in and look at the screen. 
---
You will briefly see a white background green NVIDIA logo, followed by boot information. As long as it moves past the NVIDIA logo, this checkpoint succeeded. 
```

* Another way:

```{testexpect}
[Assemble your Duckiebot](assembling-duckiebot-db21j), then [flash a Duckietown SD card](setup-duckiebot-sd-card), and finally [perform the first boot](duckiebot-boot).  
---
The Duckiebot boots successfully. 
```

```{tip}
Never skip a checkpoint!
```

(reflash-jetson-faq)=
### Troubleshooting

```{trouble}
The Jetson board is not showing up with `lsbusb`.  
---
Make sure the board is in [forced recovery mode](jetson-forced-recovery-mode) and the micro-USB to base station cable carries data.
```


```{trouble}
The Jetson board shows up with `lsbusb` after a minute or two.  
---
The micro-USB to base station cable could be finnecky. The process should be instantaneous. Change cable.
```

```{trouble}
The board shows under `lsusb`, but if I unplug the data cable and re-plug it, it doesn't show anymore.    
---
Remove the power cable before re-attaching the data cable.
```

```{trouble}
I completed the flashing of the Jetson Nano successfully, but it still does not work (e.g., static NVIDIA logo on screen). In particular, I see from the logs that my Jetson is recognized as a 2GB version, and not 4GB. 
---
The overlay patch has not been applied correctly. Make sure to set up your flashing environment according to the instructions. Do not skip any step. 
```

```{trouble}
My Jetson Nano is a 2GB version, but I purchased a 4GB version from Duckietown. I want a reimbursement!  
---
If you are sure you purchased a 4GB Jetson and Duckietown staff confirmed you were provided a 4GB Jetson, you have a 4GB Jetson that has been previously flashed incorrectly. [Reflash the Jetson](reflash-jetson-4gb). The nature of this specific problem is that the memory will not be recognized correctly, showing 2GB when the board is in fact a 4GB one.
```

(reflash-jetson-additional)=
### Additional information

Here are the full logs of a successful flash:

````{admonition} Successful flash - full logs
:class: dropdown

```bash
duckie@duckietown-ubuntu:~/jn/Linux_for_Tegra$ sudo ./flash.sh -x 0x21 jetson-nano-emmc mmcblk0p1
[sudo] password for duckie: 
###############################################################################
# L4T BSP Information:
# R32 , REVISION: 7.6
###############################################################################
# Target Board Information:
# Name: jetson-nano-emmc, Board Family: t210ref, SoC: Tegra 210, 
# OpMode: production, Boot Authentication: , 
# Disk encryption: disabled ,
###############################################################################
./tegraflash.py --chip 0x21 --applet "/home/duckie/jn/Linux_for_Tegra/bootloader/nvtboot_recovery.bin" --skipuid --cmd "dump eeprom boardinfo cvm.bin" 
Welcome to Tegra Flash
version 1.0.0
Type ? or help for help and q or quit to exit
Use ! to execute system commands
 
[   0.0026 ] Generating RCM messages
[   0.0044 ] tegrarcm --listrcm rcm_list.xml --chip 0x21 0 --download rcm /home/duckie/jn/Linux_for_Tegra/bootloader/nvtboot_recovery.bin 0 0
[   0.0047 ] RCM 0 is saved as rcm_0.rcm
[   0.0059 ] RCM 1 is saved as rcm_1.rcm
[   0.0059 ] List of rcm files are saved in rcm_list.xml
[   0.0059 ] 
[   0.0060 ] Signing RCM messages
[   0.0078 ] tegrasign --key None --list rcm_list.xml --pubkeyhash pub_key.key
[   0.0082 ] Assuming zero filled SBK key
[   0.0161 ] 
[   0.0161 ] Copying signature to RCM mesages
[   0.0178 ] tegrarcm --chip 0x21 0 --updatesig rcm_list_signed.xml
[   0.0188 ] 
[   0.0188 ] Boot Rom communication
[   0.0206 ] tegrarcm --chip 0x21 0 --rcm rcm_list_signed.xml --skipuid
[   0.0210 ] RCM version 0X210001
[   0.0630 ] Boot Rom communication completed
[   1.0716 ] 
[   1.0717 ] dump EEPROM info
[   1.0749 ] tegrarcm --oem platformdetails eeprom /home/duckie/jn/Linux_for_Tegra/bootloader/cvm.bin
[   1.0763 ] Applet version 00.01.0000
[   1.0803 ] Saved platform info in /home/duckie/jn/Linux_for_Tegra/bootloader/cvm.bin
[   1.1581 ] 
[   1.1610 ] tegrarcm --reboot recovery
[   1.1624 ] Applet version 00.01.0000
[   1.1661 ] 
Board ID(3448) version(402) 
copying bctfile(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/BCT/P3448_A00_lpddr4_204Mhz_P987.cfg)... done.
copying bootloader(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/cboot.bin)... done.
copying initrd(/home/duckie/jn/Linux_for_Tegra/bootloader/l4t_initrd.img)... done.
Making Boot image... done.
Existing sosfile(/home/duckie/jn/Linux_for_Tegra/bootloader/nvtboot_recovery.bin) reused.
copying tegraboot(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/nvtboot.bin)... done.
copying cpu_bootloader(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/cboot.bin)... done.
copying bpffile(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/sc7entry-firmware.bin)... done.
copying wb0boot(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/warmboot.bin)... done.
Existing tosfile(/home/duckie/jn/Linux_for_Tegra/bootloader/tos-mon-only.img) reused.
Existing eksfile(/home/duckie/jn/Linux_for_Tegra/bootloader/eks.img) reused.
./flash.sh: line 2663: [: : integer expression expected
copying dtbfile(/home/duckie/jn/Linux_for_Tegra/kernel/dtb/tegra210-p3448-0002-p3449-0000-b00.dtb)... done.
Copying nv_boot_control.conf to rootfs
	populating kernel to rootfs... done.
	populating initrd to rootfs... done.
	populating kernel_tegra210-p3448-0002-p3449-0000-b00.dtb to rootfs... done.
Making system.img... 
	populating rootfs from /home/duckie/jn/Linux_for_Tegra/rootfs ... 	populating /boot/extlinux/extlinux.conf ... done.
	Sync'ing system.img ... done.
	Converting RAW image to Sparse image... done.
system.img built successfully. 
Existing tbcfile(/home/duckie/jn/Linux_for_Tegra/bootloader/nvtboot_cpu.bin) reused.
copying tbcdtbfile(/home/duckie/jn/Linux_for_Tegra/kernel/dtb/tegra210-p3448-0002-p3449-0000-b00.dtb)... done.
copying cfgfile(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/cfg/flash_l4t_t210_emmc_p3448.xml) to flash.xml... done.
copying flasher(/home/duckie/jn/Linux_for_Tegra/bootloader/t210ref/cboot.bin)... done.
Existing flashapp(/home/duckie/jn/Linux_for_Tegra/bootloader/tegraflash.py) reused.
./tegraflash.py --bl cboot.bin --bct  P3448_A00_lpddr4_204Mhz_P987.cfg --odmdata 0xa4000 --bldtb kernel_tegra210-p3448-0002-p3449-0000-b00.dtb --applet nvtboot_recovery.bin  --cmd "flash; reboot"  --cfg flash.xml --chip 0x21    --bins "EBT cboot.bin; DTB tegra210-p3448-0002-p3449-0000-b00.dtb" 
saving flash command in /home/duckie/jn/Linux_for_Tegra/bootloader/flashcmd.txt
saving Windows flash command to /home/duckie/jn/Linux_for_Tegra/bootloader/flash_win.bat
assign_value: crc-flash.xml.bin 1 131056 1
printf '\x1' | dd of=crc-flash.xml.bin bs=1 seek=131056 count=1 conv=notrunc
1+0 records in
1+0 records out
1 byte copied, 5.509e-05 s, 18.2 kB/s
assign_value: crc-flash.xml.bin 0 131057 1
printf '\x0' | dd of=crc-flash.xml.bin bs=1 seek=131057 count=1 conv=notrunc
1+0 records in
1+0 records out
1 byte copied, 3.6513e-05 s, 27.4 kB/s
assign_string: crc-flash.xml.bin PTHD 131064 4
echo PTHD | dd of=crc-flash.xml.bin bs=1 seek=131064 count=4 conv=notrunc
4+0 records in
4+0 records out
4 bytes copied, 4.1125e-05 s, 97.3 kB/s
*** Flashing target device started. ***
Welcome to Tegra Flash
version 1.0.0
Type ? or help for help and q or quit to exit
Use ! to execute system commands
 
[   0.0018 ] tegrasign --getmode mode.txt --key None
[   0.0022 ] Assuming zero filled SBK key
[   0.0026 ] 
[   0.0027 ] Generating RCM messages
[   0.0042 ] tegrarcm --listrcm rcm_list.xml --chip 0x21 0 --download rcm nvtboot_recovery.bin 0 0
[   0.0045 ] RCM 0 is saved as rcm_0.rcm
[   0.0051 ] RCM 1 is saved as rcm_1.rcm
[   0.0052 ] List of rcm files are saved in rcm_list.xml
[   0.0052 ] 
[   0.0052 ] Signing RCM messages
[   0.0067 ] tegrasign --key None --list rcm_list.xml --pubkeyhash pub_key.key
[   0.0071 ] Assuming zero filled SBK key
[   0.0123 ] 
[   0.0124 ] Copying signature to RCM mesages
[   0.0139 ] tegrarcm --chip 0x21 0 --updatesig rcm_list_signed.xml
[   0.0149 ] 
[   0.0150 ] Parsing partition layout
[   0.0165 ] tegraparser --pt flash.xml.tmp
[   0.0174 ] 
[   0.0175 ] Using default ramcode: 0
[   0.0175 ] Disable BPMP dtb trim, using default dtb
[   0.0176 ] 
[   0.0176 ] Creating list of images to be signed
[   0.0192 ] tegrahost --chip 0x21 0 --partitionlayout flash.xml.bin --list images_list.xml
[   0.0417 ] 
[   0.0418 ] Generating signatures
[   0.0445 ] tegrasign --key None --list images_list.xml --pubkeyhash pub_key.key
[   0.0458 ] Assuming zero filled SBK key
[   0.1514 ] 
[   0.1514 ] Generating br-bct
[   0.1556 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.cfg --chip 0x21 0
[   0.1623 ] 
[   0.1623 ] Updating boot device parameters
[   0.1637 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatedevparam flash.xml.bin
[   0.1642 ] Warning: No sdram params
[   0.1646 ] 
[   0.1646 ] Updating bl info
[   0.1667 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updateblinfo flash.xml.bin --updatesig images_list_signed.xml
[   0.1679 ] 
[   0.1679 ] Updating secondary storage information into bct
[   0.1697 ] tegraparser --pt flash.xml.bin --chip 0x21 0 --updatecustinfo P3448_A00_lpddr4_204Mhz_P987.bct
[   0.1703 ] 
[   0.1703 ] Updating Odmdata
[   0.1718 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatefields Odmdata =0xa4000
[   0.1722 ] Warning: No sdram params
[   0.1724 ] 
[   0.1724 ] Get Signed section of bct
[   0.1738 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --listbct bct_list.xml
[   0.1744 ] 
[   0.1744 ] Signing BCT
[   0.1778 ] tegrasign --key None --list bct_list.xml --pubkeyhash pub_key.key
[   0.1781 ] Assuming zero filled SBK key
[   0.1786 ] 
[   0.1786 ] Updating BCT with signature
[   0.1801 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatesig bct_list_signed.xml
[   0.1808 ] 
[   0.1808 ] Copying signatures
[   0.1823 ] tegrahost --chip 0x21 0 --partitionlayout flash.xml.bin --updatesig images_list_signed.xml
[   0.1889 ] 
[   0.1889 ] Updating BFS information on BCT
[   0.1908 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatebfsinfo flash.xml.bin
[   0.1914 ]    BFS:
[   0.1933 ]      0: [PT ] crc-flash.xml.bin (size=131072/131072)
[   0.1939 ]      1: [TBC] nvtboot_cpu.bin.encrypt (size=80816/196608)
[   0.1944 ]      2: [RP1] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.1951 ]      3: [EBT] cboot.bin.encrypt (size=485952/655360)
[   0.1956 ]      4: [WB0] warmboot.bin.encrypt (size=3952/131072)
[   0.1961 ]      5: [BPF] sc7entry-firmware.bin.encrypt (size=3376/262144)
[   0.1966 ] BFS0: 131072 @ 2560 SUM faabf3f1 over 2883584 bytes
[   0.1970 ]    BFS:
[   0.1979 ]      0: [PT-1] crc-flash.xml.bin (size=131072/131072)
[   0.1984 ]      1: [TBC-1] nvtboot_cpu.bin.encrypt (size=80816/196608)
[   0.1989 ]      2: [RP1-1] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.1997 ]      3: [EBT-1] cboot.bin.encrypt (size=485952/655360)
[   0.2002 ]      4: [WB0-1] warmboot.bin.encrypt (size=3952/131072)
[   0.2006 ]      5: [BPF-1] sc7entry-firmware.bin.encrypt (size=3376/262144)
[   0.2012 ]      8: [VER_b] emmc_bootblob_ver.txt (size=102/32768)
[   0.2016 ]      9: [VER] emmc_bootblob_ver.txt (size=102/32768)
[   0.2020 ] BFS1: 131072 @ 8704 SUM faabf3f1 over 2981888 bytes
[   0.2023 ]    KFS:
[   0.2402 ]      0: [DTB] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.2408 ]      1: [TOS] tos-mon-only.img.encrypt (size=54208/6291456)
[   0.2413 ]      2: [EKS] eks.img (size=1028/81920)
[   0.2416 ]      3: [LNX] boot.img.encrypt (size=667648/67092480)
[   0.2421 ] KFS0: 1048576 @ 29376546 SUM 4d3bf5df over 8089600 bytes
[   0.2483 ]    KFS:
[   0.2885 ]      0: [DTB-1] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.2893 ]      1: [TOS-1] tos-mon-only.img.encrypt (size=54208/6291456)
[   0.2898 ]      2: [EKS-1] eks.img (size=1028/81920)
[   0.2900 ]      3: [LNX-1] boot.img.encrypt (size=667648/67092480)
[   0.2903 ] KFS1: 1048576 @ 29522082 SUM 4d3bf5df over 8089600 bytes
[   0.2958 ] 
[   0.2958 ] Boot Rom communication
[   0.2974 ] tegrarcm --chip 0x21 0 --rcm rcm_list_signed.xml
[   0.2977 ] BR_CID: 0x32101001644086c9180000000efd8500
[   0.3960 ] RCM version 0X210001
[   0.3963 ] Boot Rom communication completed
[   1.4051 ] 
[   1.4052 ] Sending BCTs
[   1.4083 ] tegrarcm --download bct P3448_A00_lpddr4_204Mhz_P987.bct
[   1.4098 ] Applet version 00.01.0000
[   1.4140 ] Sending bct
[   1.4145 ] [................................................] 100%
[   1.6390 ] 
[   1.6421 ] tegrahost --chip 0x21 --align cboot.bin
[   1.6442 ] 
[   1.6472 ] tegrahost --magicid EBT --appendsigheader cboot.bin cboot.bin_blheader
[   1.6542 ] 
[   1.6562 ] tegrasign --key None --list cboot.bin_list.xml
[   1.6567 ] Assuming zero filled SBK key
[   1.6735 ] 
[   1.6757 ] tegrahost --updatesigheader cboot.bin_blheader.encrypt cboot.bin_blheader.hash zerosbk
[   1.6776 ] 
[   1.6798 ] tegrahost --chip 0x21 --align tegra210-p3448-0002-p3449-0000-b00.dtb
[   1.6804 ] 
[   1.6820 ] tegrahost --magicid DTB --appendsigheader tegra210-p3448-0002-p3449-0000-b00.dtb tegra210-p3448-0002-p3449-0000-b00.dtb_blheader
[   1.6838 ] 
[   1.6857 ] tegrasign --key None --list tegra210-p3448-0002-p3449-0000-b00.dtb_list.xml
[   1.6861 ] Assuming zero filled SBK key
[   1.6948 ] 
[   1.6968 ] tegrahost --updatesigheader tegra210-p3448-0002-p3449-0000-b00.dtb_blheader.encrypt tegra210-p3448-0002-p3449-0000-b00.dtb_blheader.hash zerosbk
[   1.6980 ] 
[   1.6983 ] Sending bootloader and pre-requisite binaries
[   1.7000 ] tegrarcm --download ebt cboot.bin.encrypt 0 0 --download rp1 tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt 0
[   1.7005 ] Applet version 00.01.0000
[   1.7027 ] Sending ebt
[   1.7031 ] [................................................] 100%
[   1.8111 ] Sending rp1
[   1.8154 ] [................................................] 100%
[   1.8770 ] 
[   1.8801 ] tegrarcm --boot recovery
[   1.8815 ] Applet version 00.01.0000
[   1.8858 ] 
[   1.8859 ] Retrieving storage infomation
[   1.8886 ] tegrarcm --oem platformdetails storage storage_info.bin
[   1.8901 ] Applet is not running on device. Continue with Bootloader
[   2.5221 ] 
[   2.5314 ] tegradevflash --oem platformdetails storage storage_info.bin
[   2.5319 ] Cboot version 00.01.0000
[   2.5354 ] Saved platform info in storage_info.bin
[   2.5368 ] 
[   2.5368 ] Flashing the device
[   2.5388 ] tegradevflash --pt flash.xml.bin --storageinfo storage_info.bin --create
[   2.5394 ] Cboot version 00.01.0000
[   2.5413 ] Writing partition GPT with gpt.bin
[   2.5416 ] [................................................] 100%
[   2.5475 ] Writing partition PT with crc-flash.xml.bin
[   3.2979 ] [................................................] 100%
[   3.3077 ] Writing partition PT-1 with crc-flash.xml.bin
[   3.3177 ] [................................................] 100%
[   3.3393 ] Writing partition NVC with nvtboot.bin.encrypt
[   3.3827 ] [................................................] 100%
[   3.4008 ] Writing partition TBC with nvtboot_cpu.bin.encrypt
[   3.4320 ] [................................................] 100%
[   3.4532 ] Writing partition RP1 with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[   3.5002 ] [................................................] 100%
[   3.5260 ] Writing partition EBT with cboot.bin.encrypt
[   3.5766 ] [................................................] 100%
[   3.6106 ] Writing partition WB0 with warmboot.bin.encrypt
[   3.6653 ] [................................................] 100%
[   3.6824 ] Writing partition BPF with sc7entry-firmware.bin.encrypt
[   3.7301 ] [................................................] 100%
[   3.7471 ] Writing partition NVC-1 with nvtboot.bin.encrypt
[   3.7946 ] [................................................] 100%
[   3.8185 ] Writing partition TBC-1 with nvtboot_cpu.bin.encrypt
[   3.8824 ] [................................................] 100%
[   3.9030 ] Writing partition RP1-1 with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[   3.9649 ] [................................................] 100%
[   3.9909 ] Writing partition EBT-1 with cboot.bin.encrypt
[   4.0531 ] [................................................] 100%
[   4.0869 ] Writing partition WB0-1 with warmboot.bin.encrypt
[   4.1528 ] [................................................] 100%
[   4.1701 ] Writing partition BPF-1 with sc7entry-firmware.bin.encrypt
[   4.2319 ] [................................................] 100%
[   4.2488 ] Writing partition VER_b with emmc_bootblob_ver.txt
[   4.3093 ] [................................................] 100%
[   4.3265 ] Writing partition VER with emmc_bootblob_ver.txt
[   4.3792 ] [................................................] 100%
[   4.3968 ] Writing partition APP with system.img
[   4.4459 ] [................................................] 100%
[ 204.6738 ] Writing partition DTB with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[ 205.9744 ] [................................................] 100%
[ 205.9930 ] Writing partition TOS with tos-mon-only.img.encrypt
[ 206.0333 ] [................................................] 100%
[ 206.0457 ] Warning: EKS partition magic header mismatch!
[ 206.0833 ] Writing partition EKS with eks.img
[ 206.0842 ] [................................................] 100%
[ 206.0935 ] Writing partition LNX with boot.img.encrypt
[ 206.1282 ] [................................................] 100%
[ 206.1641 ] Writing partition DTB-1 with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[ 206.2124 ] [................................................] 100%
[ 206.2308 ] Writing partition TOS-1 with tos-mon-only.img.encrypt
[ 206.2707 ] [................................................] 100%
[ 206.2831 ] Writing partition EKS-1 with eks.img
[ 206.3190 ] [................................................] 100%
[ 206.3296 ] Writing partition LNX-1 with boot.img.encrypt
[ 206.3652 ] [................................................] 100%
[ 206.3995 ] Writing partition BMP with bmp.blob
[ 206.4417 ] [................................................] 100%
[ 206.4653 ] Writing partition RP4 with rp4.blob
[ 206.5027 ] [................................................] 100%
[ 206.5554 ] 
[ 206.5583 ] tegradevflash --write BCT P3448_A00_lpddr4_204Mhz_P987.bct
[ 206.5596 ] Cboot version 00.01.0000
[ 206.6606 ] Writing partition BCT with P3448_A00_lpddr4_204Mhz_P987.bct
[ 206.6627 ] [................................................] 100%
[ 207.0590 ] 
[ 207.0591 ] Flashing completed

[ 207.0592 ] Coldbooting the device
[ 207.0622 ] tegradevflash --reboot coldboot
[ 207.0635 ] Cboot version 00.01.0000
[ 207.0673 ] 
*** The target t210ref has been flashed successfully. ***
Reset the board to boot from internal eMMC.
```
````


[serial-cable-link]: https://www.amazon.com/HiLetgo-CP2102-Converter-Adapter-Downloader/dp/B00LODGRV8/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.1ac62dee-1169-4bf4-91b9-84fe33c930b1:amzn1.sym.1ac62dee-1169-4bf4-91b9-84fe33c930b1&crid=141181LA9EWAU&cv_ct_cx=usb+to+serial&keywords=usb+to+serial&pd_rd_i=B00LODGRV8&pd_rd_r=c5bf6f43-cac0-465a-a2a4-62d11e9cf4c0&pd_rd_w=jhgf3&pd_rd_wg=bjtnY&pf_rd_p=1ac62dee-1169-4bf4-91b9-84fe33c930b1&pf_rd_r=5BQHEBJ7FGCESHQY2E67&psc=1&qid=1743589611&sbo=RZvfv//HxDF+O5021pAnSA==&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&sprefix=usb+tose,aps,225&sr=1-3-6024b2a3-78e4-4fed-8fed-e1613be3bcce-spons