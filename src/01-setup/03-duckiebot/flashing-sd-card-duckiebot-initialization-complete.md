(setup-db-sd-card-flashing-complete)=
# The Complete Way - Initialization

```{seo}
:description: Instructions on how to flash an SD card to initialize a Duckiebot, Duckiedrone, Traffic Light or Watchtower.
:keywords: Duckietown, Duckiebot, Duckiedrone, flashing, initialization, SD card, Traffic Light, Watchtower, dts init sd card, dts init_sd_card
```

```{needget}
* [Functional DTS installation](setup-dts).
* An SD card with at least `64 GB` of space.
* An SD card adapter appropriate for the computer you are using to flash the SD card
* A broadband internet connection
* 20 - 40 mins, depending on internet connection speed
* At least 40 GB of free space on your hard drive before starting
---
An initialized SD card for your Duckietown robot.
```

Use this procedure if you want full control over the configuration settings of your robot.


(initialize-sd-card-video)=
## Burning the SD card with `dts init_sd_card`

```{vimeo} 526698325
```

```{note}
The default username (not to be confused with the hostname/robotname) and password are `duckie` and `quackquack`, respectively. This is useful if you want to later `ssh` into your robot.
```



Start by plugging the SD card into your computer using a SD card reader or the USB to microSD card adapter provided in your Duckiebot kit. Make sure the SD card is detected before proceeding.

Then, open a terminal and use the command:

```shell
dts init_sd_card --hostname HOSTNAME --type TYPE --configuration CONFIGURATION --wifi WIFI[,WIFI2,...,WIFIN] [--country COUNTRY] [--version VERSION]
```

Where:

* `--hostname` is the name of the robot you are flashing the SD card for. 

```{attention}
The `HOSTNAME`, or robot name, is going to be used extensively in future interactions with the robot, and can only be changed by reflashing your SD card. 

Choose a hostname for your robot such that it:

* Is unique within a fleet of Duckiebots connected to the same network
* Is fully lowercase
* Starts with a letter
* Contains only letters, numbers or underscores

For example:

* ✅ `myduckiebot`
* ✅ `myduckiebot01`
* ❌ `123bot`
* ❌ `MyDuckiebot`
* ❌ `Whatabot!`
```

* `--type` is what kind of robot you are flashing. Types are `duckiebot` (default), `watchtower`, `traffic_light`.

* `--configuration` is the model of your robot. This is associated with `--type` option. Options for `duckiebot` are, e.g., `DB21J`, `DBR4`, `DB21M`, `DB19`, or `DB18`.

```{attention}
* If you have a Duckiebot with a **4GB** Jetson Nano - the model is **DB21J**
* If you have a Duckiebot with a **2GB** Jetson Nano (you shouldn't) - the model is **DB21M**
* If you are not using a Jetson Nano, the model is the model of your Duckiebot (e.g., DB19 or DBR4)
* If you are not sure what Duckiebot you have, refer to [](duckiebot-configurations) or [reach out to support](how-to-get-help).
```

* `--wifi` is a comma-separated list of Wi-Fi networks, each passed in the format `wifiname:wifipassword`. E.g., (default) `duckietown:quackquack`. [Networks can be edited after the robot is initialized too](db-troubleshooting-network), without needing to reflash the SD card. Nonetheless, making sure your initial credentials are correct simplifies next steps. 

````{attention}
* If you plan on the robot connecting over different networks (e.g., at home and in class), list all your networks *without spaces after the commas*:

```shell
dts init_sd_card ... --wifi duckietown:quackquack,myhomenetwork:myhomepassword,myuninetwork:myunipassword
```
* If your network `SSID` contains, e.g., spaces, use quotation marks:

```shell
dts init_sd_card ... -wifi "my fancy network name:quackquack"
```

* Networks in the list can support additional arguments:

      - Open networks (no password): "ssid"
      - PSK (Pre-shared key) protected networks: "ssid:psk"
      - EAP (Extensible Authentication Protocol) protected networks: "ssid:username:password"
````

* `--country` is an optional argument but highly recommended. Neglecting this sometimes will result in specific Wi-Fi hotspots not being seen by the Duckiebot. `COUNTRY` arguments could be, e.g., `CA` for Canada, `CH` for Switzerland, or `US` for the United States of America. A full list of codes can be found, e.g., on Wikipedia: [ISO 3166-1 alpha-2 codes](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2).

* `--version` is an optional numeric argument to download a specific version of the Duckietown image for the specific `CONFIGURATION` and `TYPE`. In default (recommended), it will download the latest available. Example `VERSION` parameters could be `2.0.1` or `1.4.2`. 

Additional options for `init_sd_card` exist. For a full list of the options, run:

    dts init_sd_card --help

## The flashing procedure

After you run the `dts init_sd_card` command, follow the instructions that appear on screen.

### Legal things

Part of this procedure includes accepting the [Duckietown Software License](https://duckietown.com/sw-license/), [Terms and Conditions](https://duckietown.com/terms-and-conditions/) and [Privacy Policy](https://duckietown.com/privacy/), as well as robot configuration-specific licenses due to the presence of third
party software in the SD card. Acceptance is mandatory, resistance is futile.

### Downloading the compressed image

The process will start by downloading the image to your `/tmp/duckietown/` folder. Note that if a compliant image is detected in that path, this step will be skipped. It is not necessary to re-download the image repeatedly if flashing multiple SD cards in the same session. 

### Extracting the archive 

The process will continue with extracting the `.img` image from the downloaded file. 

```{warning}
You might feel tempted to abort the procedure at this stage and flash this `.img` file to an SD card using a third-party tool, e.g., Balena Etcher. Resist this temptation, it will not work (yet). Carry on reading. 
```

### Writing the image

At this stage you will be prompted to choose the device where to flash the image file to. All storage devices connected to your computer are candidates. 

Given the danger (from data loss to OS files corruption) of choosing a wrong device, the procedure will prompt you for the nominal size of the SD card you want to flash the image to. Devices that do not match the given size will not be shown. A standard Duckietown SD is nominally `64` GB.

A list of devices with capacity close to the number provided will be shown. Type in or copy-paste the device name from the list and press <kbd>Enter</kbd>.

```{attention}
You can choose to write the image to a file instead of a device, e.g., by typing in `/my/nonprotected/path/duckietown_image_9.9.9.img`. Once this file is created, it can be successfully flashed to a device using any third-party tool.
```
### Finalizing the `init_sd_card` process

On successful end of the procedure, the drive will be automatically ejected, and you will be instructed to remove the SD card from the SD card reader and insert it, e.g., into the Duckiebot's SD card slot.

If you experience any issues while flashing the SD card, make sure you check the [](sd-card-flashing-troubleshooting) section before asking for help on Stack Overflow.

(sd-card-flashing-troubleshooting)=
## Troubleshooting

```{trouble}
- The SD card doesn't seem to be written.
- The flashing process seemed too fast, there is no data on my SD card.
---
- Check if your SD card adapter has a write protection switch.
- Make sure you selected the correct drive name during the flashing procedure.
```

```{trouble}
I am using a microSD to SD card adapter with write protection disabled but the SD card does not seem to be initialized after running the procedure.
---
Try again, making sure that you enter the correct drive name during the procedure.
```

```{trouble}
The procedure fails due to a "Bad archive" error.
---
Try again using the `--no-cache` option.
```

```{trouble}
The verification process fails with error `Please set up a token using "dts tok set"`.
---
Make sure you completed the Duckietown token setup procedure [](dt-account).
```

Additional information is available at [](db-troubleshooting-network).