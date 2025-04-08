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

    sudo ./flash.sh -x 0x21 ${BOARD} sda1

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
tani@tani-ubuntu:~/jn/Linux_for_Tegra$ sudo ./flash.sh -x 0x21 jetson-nano-emmc sda1
###############################################################################
# L4T BSP Information:
# R32 , REVISION: 7.6
###############################################################################
# Target Board Information:
# Name: jetson-nano-emmc, Board Family: t210ref, SoC: Tegra 210, 
# OpMode: production, Boot Authentication: , 
# Disk encryption: disabled ,
###############################################################################
./tegraflash.py --chip 0x21 --applet "/home/tani/jn/Linux_for_Tegra/bootloader/nvtboot_recovery.bin" --skipuid --cmd "dump eeprom boardinfo cvm.bin" 
Welcome to Tegra Flash
version 1.0.0
Type ? or help for help and q or quit to exit
Use ! to execute system commands
 
[   0.0034 ] Generating RCM messages
[   0.0053 ] tegrarcm --listrcm rcm_list.xml --chip 0x21 0 --download rcm /home/tani/jn/Linux_for_Tegra/bootloader/nvtboot_recovery.bin 0 0
[   0.0057 ] RCM 0 is saved as rcm_0.rcm
[   0.0069 ] RCM 1 is saved as rcm_1.rcm
[   0.0069 ] List of rcm files are saved in rcm_list.xml
[   0.0069 ] 
[   0.0069 ] Signing RCM messages
[   0.0086 ] tegrasign --key None --list rcm_list.xml --pubkeyhash pub_key.key
[   0.0090 ] Assuming zero filled SBK key
[   0.0162 ] 
[   0.0162 ] Copying signature to RCM mesages
[   0.0178 ] tegrarcm --chip 0x21 0 --updatesig rcm_list_signed.xml
[   0.0190 ] 
[   0.0190 ] Boot Rom communication
[   0.0207 ] tegrarcm --chip 0x21 0 --rcm rcm_list_signed.xml --skipuid
[   0.0210 ] RCM version 0X210001
[   0.0626 ] Boot Rom communication completed
[   1.0711 ] 
[   1.0712 ] dump EEPROM info
[   1.0745 ] tegrarcm --oem platformdetails eeprom /home/tani/jn/Linux_for_Tegra/bootloader/cvm.bin
[   1.0758 ] Applet version 00.01.0000
[   1.0795 ] Saved platform info in /home/tani/jn/Linux_for_Tegra/bootloader/cvm.bin
[   1.1654 ] 
[   1.1684 ] tegrarcm --reboot recovery
[   1.1698 ] Applet version 00.01.0000
[   1.1742 ] 
Board ID(3448) version(402) 
copying bctfile(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/BCT/P3448_A00_lpddr4_204Mhz_P987.cfg)... done.
copying bootloader(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/cboot.bin)... done.
copying initrd(/home/tani/jn/Linux_for_Tegra/bootloader/l4t_initrd.img)... done.
Making Boot image... done.
Existing sosfile(/home/tani/jn/Linux_for_Tegra/bootloader/nvtboot_recovery.bin) reused.
copying tegraboot(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/nvtboot.bin)... done.
copying cpu_bootloader(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/cboot.bin)... done.
copying bpffile(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/sc7entry-firmware.bin)... done.
copying wb0boot(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/warmboot.bin)... done.
Existing tosfile(/home/tani/jn/Linux_for_Tegra/bootloader/tos-mon-only.img) reused.
Existing eksfile(/home/tani/jn/Linux_for_Tegra/bootloader/eks.img) reused.
./flash.sh: line 2663: [: : integer expression expected
copying dtbfile(/home/tani/jn/Linux_for_Tegra/kernel/dtb/tegra210-p3448-0002-p3449-0000-b00.dtb)... done.
Copying nv_boot_control.conf to rootfs
generating system.img for booting... 
Making system.img... 
	populating rootfs from /tmp/tmp.g5o6AwlRHm ... 	populating /boot/extlinux/extlinux.conf ... done.
	Sync'ing system.img ... done.
	Converting RAW image to Sparse image... done.
system.img built successfully. 
Existing tbcfile(/home/tani/jn/Linux_for_Tegra/bootloader/nvtboot_cpu.bin) reused.
copying tbcdtbfile(/home/tani/jn/Linux_for_Tegra/kernel/dtb/tegra210-p3448-0002-p3449-0000-b00.dtb)... done.
copying cfgfile(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/cfg/flash_l4t_t210_emmc_p3448.xml) to flash.xml... done.
copying flasher(/home/tani/jn/Linux_for_Tegra/bootloader/t210ref/cboot.bin)... done.
Existing flashapp(/home/tani/jn/Linux_for_Tegra/bootloader/tegraflash.py) reused.
./tegraflash.py --bl cboot.bin --bct  P3448_A00_lpddr4_204Mhz_P987.cfg --odmdata 0xa4000 --bldtb kernel_tegra210-p3448-0002-p3449-0000-b00.dtb --applet nvtboot_recovery.bin  --cmd "flash; reboot"  --cfg flash.xml --chip 0x21    --bins "EBT cboot.bin; DTB tegra210-p3448-0002-p3449-0000-b00.dtb" 
saving flash command in /home/tani/jn/Linux_for_Tegra/bootloader/flashcmd.txt
saving Windows flash command to /home/tani/jn/Linux_for_Tegra/bootloader/flash_win.bat
assign_value: crc-flash.xml.bin 1 131056 1
printf '\x1' | dd of=crc-flash.xml.bin bs=1 seek=131056 count=1 conv=notrunc
1+0 records in
1+0 records out
1 byte copied, 5.6995e-05 s, 17.5 kB/s
assign_value: crc-flash.xml.bin 0 131057 1
printf '\x0' | dd of=crc-flash.xml.bin bs=1 seek=131057 count=1 conv=notrunc
1+0 records in
1+0 records out
1 byte copied, 3.266e-05 s, 30.6 kB/s
assign_string: crc-flash.xml.bin PTHD 131064 4
echo PTHD | dd of=crc-flash.xml.bin bs=1 seek=131064 count=4 conv=notrunc
4+0 records in
4+0 records out
4 bytes copied, 3.7921e-05 s, 105 kB/s
*** Flashing target device started. ***
Welcome to Tegra Flash
version 1.0.0
Type ? or help for help and q or quit to exit
Use ! to execute system commands
 
[   0.0019 ] tegrasign --getmode mode.txt --key None
[   0.0022 ] Assuming zero filled SBK key
[   0.0026 ] 
[   0.0027 ] Generating RCM messages
[   0.0042 ] tegrarcm --listrcm rcm_list.xml --chip 0x21 0 --download rcm nvtboot_recovery.bin 0 0
[   0.0045 ] RCM 0 is saved as rcm_0.rcm
[   0.0051 ] RCM 1 is saved as rcm_1.rcm
[   0.0053 ] List of rcm files are saved in rcm_list.xml
[   0.0053 ] 
[   0.0053 ] Signing RCM messages
[   0.0069 ] tegrasign --key None --list rcm_list.xml --pubkeyhash pub_key.key
[   0.0072 ] Assuming zero filled SBK key
[   0.0118 ] 
[   0.0119 ] Copying signature to RCM mesages
[   0.0135 ] tegrarcm --chip 0x21 0 --updatesig rcm_list_signed.xml
[   0.0145 ] 
[   0.0145 ] Parsing partition layout
[   0.0159 ] tegraparser --pt flash.xml.tmp
[   0.0166 ] 
[   0.0167 ] Using default ramcode: 0
[   0.0168 ] Disable BPMP dtb trim, using default dtb
[   0.0168 ] 
[   0.0168 ] Creating list of images to be signed
[   0.0187 ] tegrahost --chip 0x21 0 --partitionlayout flash.xml.bin --list images_list.xml
[   0.0276 ] 
[   0.0276 ] Generating signatures
[   0.0292 ] tegrasign --key None --list images_list.xml --pubkeyhash pub_key.key
[   0.0295 ] Assuming zero filled SBK key
[   0.1184 ] 
[   0.1184 ] Generating br-bct
[   0.1228 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.cfg --chip 0x21 0
[   0.1306 ] 
[   0.1306 ] Updating boot device parameters
[   0.1323 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatedevparam flash.xml.bin
[   0.1326 ] Warning: No sdram params
[   0.1328 ] 
[   0.1328 ] Updating bl info
[   0.1344 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updateblinfo flash.xml.bin --updatesig images_list_signed.xml
[   0.1358 ] 
[   0.1358 ] Updating secondary storage information into bct
[   0.1378 ] tegraparser --pt flash.xml.bin --chip 0x21 0 --updatecustinfo P3448_A00_lpddr4_204Mhz_P987.bct
[   0.1385 ] 
[   0.1385 ] Updating Odmdata
[   0.1406 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatefields Odmdata =0xa4000
[   0.1410 ] Warning: No sdram params
[   0.1412 ] 
[   0.1412 ] Get Signed section of bct
[   0.1427 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --listbct bct_list.xml
[   0.1441 ] 
[   0.1441 ] Signing BCT
[   0.1485 ] tegrasign --key None --list bct_list.xml --pubkeyhash pub_key.key
[   0.1494 ] Assuming zero filled SBK key
[   0.1510 ] 
[   0.1510 ] Updating BCT with signature
[   0.1532 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatesig bct_list_signed.xml
[   0.1549 ] 
[   0.1549 ] Copying signatures
[   0.1571 ] tegrahost --chip 0x21 0 --partitionlayout flash.xml.bin --updatesig images_list_signed.xml
[   0.1741 ] 
[   0.1742 ] Updating BFS information on BCT
[   0.1763 ] tegrabct --bct P3448_A00_lpddr4_204Mhz_P987.bct --chip 0x21 0 --updatebfsinfo flash.xml.bin
[   0.1771 ]    BFS:
[   0.1806 ]      0: [PT ] crc-flash.xml.bin (size=131072/131072)
[   0.1813 ]      1: [TBC] nvtboot_cpu.bin.encrypt (size=80816/196608)
[   0.1818 ]      2: [RP1] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.1825 ]      3: [EBT] cboot.bin.encrypt (size=485952/655360)
[   0.1829 ]      4: [WB0] warmboot.bin.encrypt (size=3952/131072)
[   0.1832 ]      5: [BPF] sc7entry-firmware.bin.encrypt (size=3376/262144)
[   0.1836 ] BFS0: 131072 @ 2560 SUM e53bd17c over 2883584 bytes
[   0.1840 ]    BFS:
[   0.1861 ]      0: [PT-1] crc-flash.xml.bin (size=131072/131072)
[   0.1865 ]      1: [TBC-1] nvtboot_cpu.bin.encrypt (size=80816/196608)
[   0.1869 ]      2: [RP1-1] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.1875 ]      3: [EBT-1] cboot.bin.encrypt (size=485952/655360)
[   0.1878 ]      4: [WB0-1] warmboot.bin.encrypt (size=3952/131072)
[   0.1881 ]      5: [BPF-1] sc7entry-firmware.bin.encrypt (size=3376/262144)
[   0.1885 ]      8: [VER_b] emmc_bootblob_ver.txt (size=102/32768)
[   0.1892 ]      9: [VER] emmc_bootblob_ver.txt (size=102/32768)
[   0.1898 ] BFS1: 131072 @ 8704 SUM e53bd17c over 2981888 bytes
[   0.1904 ]    KFS:
[   0.2272 ]      0: [DTB] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.2277 ]      1: [TOS] tos-mon-only.img.encrypt (size=54208/6291456)
[   0.2282 ]      2: [EKS] eks.img (size=1028/81920)
[   0.2285 ]      3: [LNX] boot.img.encrypt (size=667648/67092480)
[   0.2289 ] KFS0: 1048576 @ 29376546 SUM 5040b3ff over 8089600 bytes
[   0.2330 ]    KFS:
[   0.2668 ]      0: [DTB-1] kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt (size=261712/1048576)
[   0.2675 ]      1: [TOS-1] tos-mon-only.img.encrypt (size=54208/6291456)
[   0.2679 ]      2: [EKS-1] eks.img (size=1028/81920)
[   0.2681 ]      3: [LNX-1] boot.img.encrypt (size=667648/67092480)
[   0.2686 ] KFS1: 1048576 @ 29522082 SUM 5040b3ff over 8089600 bytes
[   0.2733 ] 
[   0.2733 ] Boot Rom communication
[   0.2752 ] tegrarcm --chip 0x21 0 --rcm rcm_list_signed.xml
[   0.2755 ] BR_CID: 0x32101001644086c9180000000efd8500
[   0.3743 ] RCM version 0X210001
[   0.3750 ] Boot Rom communication completed
[   1.3830 ] 
[   1.3831 ] Sending BCTs
[   1.3859 ] tegrarcm --download bct P3448_A00_lpddr4_204Mhz_P987.bct
[   1.3872 ] Applet version 00.01.0000
[   1.3911 ] Sending bct
[   1.3915 ] [................................................] 100%
[   1.6159 ] 
[   1.6193 ] tegrahost --chip 0x21 --align cboot.bin
[   1.6211 ] 
[   1.6237 ] tegrahost --magicid EBT --appendsigheader cboot.bin cboot.bin_blheader
[   1.6298 ] 
[   1.6317 ] tegrasign --key None --list cboot.bin_list.xml
[   1.6322 ] Assuming zero filled SBK key
[   1.6482 ] 
[   1.6502 ] tegrahost --updatesigheader cboot.bin_blheader.encrypt cboot.bin_blheader.hash zerosbk
[   1.6517 ] 
[   1.6539 ] tegrahost --chip 0x21 --align tegra210-p3448-0002-p3449-0000-b00.dtb
[   1.6547 ] 
[   1.6565 ] tegrahost --magicid DTB --appendsigheader tegra210-p3448-0002-p3449-0000-b00.dtb tegra210-p3448-0002-p3449-0000-b00.dtb_blheader
[   1.6582 ] 
[   1.6601 ] tegrasign --key None --list tegra210-p3448-0002-p3449-0000-b00.dtb_list.xml
[   1.6605 ] Assuming zero filled SBK key
[   1.6684 ] 
[   1.6703 ] tegrahost --updatesigheader tegra210-p3448-0002-p3449-0000-b00.dtb_blheader.encrypt tegra210-p3448-0002-p3449-0000-b00.dtb_blheader.hash zerosbk
[   1.6714 ] 
[   1.6717 ] Sending bootloader and pre-requisite binaries
[   1.6735 ] tegrarcm --download ebt cboot.bin.encrypt 0 0 --download rp1 tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt 0
[   1.6739 ] Applet version 00.01.0000
[   1.6760 ] Sending ebt
[   1.6764 ] [................................................] 100%
[   1.7854 ] Sending rp1
[   1.7897 ] [................................................] 100%
[   1.8517 ] 
[   1.8547 ] tegrarcm --boot recovery
[   1.8560 ] Applet version 00.01.0000
[   1.8604 ] 
[   1.8605 ] Retrieving storage infomation
[   1.8631 ] tegrarcm --oem platformdetails storage storage_info.bin
[   1.8645 ] Applet is not running on device. Continue with Bootloader
[   2.4968 ] 
[   2.5061 ] tegradevflash --oem platformdetails storage storage_info.bin
[   2.5068 ] Cboot version 00.01.0000
[   2.5111 ] Saved platform info in storage_info.bin
[   2.5125 ] 
[   2.5125 ] Flashing the device
[   2.5146 ] tegradevflash --pt flash.xml.bin --storageinfo storage_info.bin --create
[   2.5155 ] Cboot version 00.01.0000
[   2.5180 ] Writing partition GPT with gpt.bin
[   2.5189 ] [................................................] 100%
[   2.5262 ] Writing partition PT with crc-flash.xml.bin
[   3.2718 ] [................................................] 100%
[   3.2817 ] Writing partition PT-1 with crc-flash.xml.bin
[   3.2933 ] [................................................] 100%
[   3.3166 ] Writing partition NVC with nvtboot.bin.encrypt
[   3.3577 ] [................................................] 100%
[   3.3762 ] Writing partition TBC with nvtboot_cpu.bin.encrypt
[   3.4072 ] [................................................] 100%
[   3.4269 ] Writing partition RP1 with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[   3.4756 ] [................................................] 100%
[   3.5014 ] Writing partition EBT with cboot.bin.encrypt
[   3.5527 ] [................................................] 100%
[   3.5897 ] Writing partition WB0 with warmboot.bin.encrypt
[   3.6432 ] [................................................] 100%
[   3.6600 ] Writing partition BPF with sc7entry-firmware.bin.encrypt
[   3.7081 ] [................................................] 100%
[   3.7247 ] Writing partition NVC-1 with nvtboot.bin.encrypt
[   3.7728 ] [................................................] 100%
[   3.7970 ] Writing partition TBC-1 with nvtboot_cpu.bin.encrypt
[   3.8589 ] [................................................] 100%
[   3.8789 ] Writing partition RP1-1 with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[   3.9402 ] [................................................] 100%
[   3.9681 ] Writing partition EBT-1 with cboot.bin.encrypt
[   4.0314 ] [................................................] 100%
[   4.0694 ] Writing partition WB0-1 with warmboot.bin.encrypt
[   4.1366 ] [................................................] 100%
[   4.1548 ] Writing partition BPF-1 with sc7entry-firmware.bin.encrypt
[   4.2165 ] [................................................] 100%
[   4.2344 ] Writing partition VER_b with emmc_bootblob_ver.txt
[   4.2951 ] [................................................] 100%
[   4.3135 ] Writing partition VER with emmc_bootblob_ver.txt
[   4.3653 ] [................................................] 100%
[   4.3841 ] Writing partition APP with system.img
[   4.4349 ] [................................................] 100%
[   7.3784 ] Writing partition DTB with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[   8.9185 ] [................................................] 100%
[   8.9381 ] Writing partition TOS with tos-mon-only.img.encrypt
[   8.9774 ] [................................................] 100%
[   8.9901 ] Warning: EKS partition magic header mismatch!
[   9.0258 ] Writing partition EKS with eks.img
[   9.0270 ] [................................................] 100%
[   9.0368 ] Writing partition LNX with boot.img.encrypt
[   9.0729 ] [................................................] 100%
[   9.1121 ] Writing partition DTB-1 with kernel_tegra210-p3448-0002-p3449-0000-b00.dtb.encrypt
[   9.1572 ] [................................................] 100%
[   9.1780 ] Writing partition TOS-1 with tos-mon-only.img.encrypt
[   9.2170 ] [................................................] 100%
[   9.2303 ] Writing partition EKS-1 with eks.img
[   9.2679 ] [................................................] 100%
[   9.2801 ] Writing partition LNX-1 with boot.img.encrypt
[   9.3170 ] [................................................] 100%
[   9.3577 ] Writing partition BMP with bmp.blob
[   9.4061 ] [................................................] 100%
[   9.4325 ] Writing partition RP4 with rp4.blob
[   9.4703 ] [................................................] 100%
[   9.5249 ] 
[   9.5282 ] tegradevflash --write BCT P3448_A00_lpddr4_204Mhz_P987.bct
[   9.5296 ] Cboot version 00.01.0000
[   9.6306 ] Writing partition BCT with P3448_A00_lpddr4_204Mhz_P987.bct
[   9.6330 ] [................................................] 100%
[  10.0292 ] 
[  10.0293 ] Flashing completed

[  10.0294 ] Coldbooting the device
[  10.0324 ] tegradevflash --reboot coldboot
[  10.0339 ] Cboot version 00.01.0000
[  10.0377 ] 
*** The target t210ref has been flashed successfully. ***
Make the target filesystem available to the device and reset the board to boot from external sda1.

```
````


[serial-cable-link]: https://www.amazon.com/HiLetgo-CP2102-Converter-Adapter-Downloader/dp/B00LODGRV8/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.1ac62dee-1169-4bf4-91b9-84fe33c930b1:amzn1.sym.1ac62dee-1169-4bf4-91b9-84fe33c930b1&crid=141181LA9EWAU&cv_ct_cx=usb+to+serial&keywords=usb+to+serial&pd_rd_i=B00LODGRV8&pd_rd_r=c5bf6f43-cac0-465a-a2a4-62d11e9cf4c0&pd_rd_w=jhgf3&pd_rd_wg=bjtnY&pf_rd_p=1ac62dee-1169-4bf4-91b9-84fe33c930b1&pf_rd_r=5BQHEBJ7FGCESHQY2E67&psc=1&qid=1743589611&sbo=RZvfv//HxDF+O5021pAnSA==&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&sprefix=usb+tose,aps,225&sr=1-3-6024b2a3-78e4-4fed-8fed-e1613be3bcce-spons
