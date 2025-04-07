```{seo}
:description: How to reflash a Jetson Nano 4GB development kit.
:keywords: Duckietown, Duckiebot, Nvidia Jetson Nano, Jetson Nano, Jetson Nano development kit, Jetson does not boot, white screen nvidia logo, jetson nano 4gb reboots continuously
```

(reflash-jetson-4gb)=
# Debug - Re-flash NVIDA Jetson Nano 4GB development kit

```{needget}
* A NVIDIA Jetson Nano 4GB development kit with onboard `emmc` memory (hereafter, the "Jetson")
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

* **What**: This procedure flashes the Jetson Nano Development Kit's onboard emmc memory with a basic Ubuntu operating system (OS), necessary for the board to boot from SD card. 

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
## How to flash the Jetson Nano 4GB Development Kit with emmc memory

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

To (over)write the Jetson's (carrier board...) onboard memory, which in the case of this document is assumed to be a 16GB emmc hard drive, we need to power on the Jetson while in "Forced Recovery" mode. To do so, we need to first identify the `FC REC` pin placed underneath the Jetson Nano module, near the SD card slot, as shown in {numref}`fig:02-JN-ForcedRecoveryPins`.

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

The process takes about 2-4 minutes, depending on the speed of the base station used. Successful flashing will result in a `SUCCESS` on the terminal after a long process.

```{note}
The Jetson board will restart immediately after the process is complete. If you have an HDMI cable and screen plugged in and would like to see if the process worked, remove the short from the `FC REC` and `GND` pins while the board is being flashed (it is safe to do so).
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






[serial-cable-link]: https://www.amazon.com/HiLetgo-CP2102-Converter-Adapter-Downloader/dp/B00LODGRV8/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.1ac62dee-1169-4bf4-91b9-84fe33c930b1:amzn1.sym.1ac62dee-1169-4bf4-91b9-84fe33c930b1&crid=141181LA9EWAU&cv_ct_cx=usb+to+serial&keywords=usb+to+serial&pd_rd_i=B00LODGRV8&pd_rd_r=c5bf6f43-cac0-465a-a2a4-62d11e9cf4c0&pd_rd_w=jhgf3&pd_rd_wg=bjtnY&pf_rd_p=1ac62dee-1169-4bf4-91b9-84fe33c930b1&pf_rd_r=5BQHEBJ7FGCESHQY2E67&psc=1&qid=1743589611&sbo=RZvfv//HxDF+O5021pAnSA==&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&sprefix=usb+tose,aps,225&sr=1-3-6024b2a3-78e4-4fed-8fed-e1613be3bcce-spons