```{seo}
:description: Instructions on how to flash an SD card to initialize a Duckiebot with the fast and easy approach, trading off time for customizability.
:keywords: Duckietown, Duckiebot, flashing, initialization, SD card, Watchtower, dts init sd card, dts init_sd_card
```

```{needget}
* An SD card with at least `64 GB` of space
* An SD card adapter appropriate for the computer you are using to flash the SD card
* A broadband internet connection
* 5-15 mins, depending on your internet connection speed
* At least 26 GB of free space on your hard drive before starting
---
An initialized SD card for your Duckiebot with default configuration settings.
```

(setup-db-sd-card-flashing-fast)=
# The Fast Way - Initialization

Use this procedure if you want a quicker result, and do not mind having a default robot name. 

```{tip}
Robots on the same network must have unique names. Do not follow this procedure if you plan on having multiple Duckiebots on the same network.
```

```{attention}
By proceeding with these instructions you are accepting the [Duckietown terms of use](initialization-tos). 
```

(initialize-sd-card-video-fast)=
## Image download

1. Read and understand the [](initialization-tos) before proceeding. For any questions or doubts, [reach out](mailto:info@duckietown.com).

(initialization-tos)=
### Legal things - Accepting Duckietown legal terms

By downloading this image you accept the [Duckietown Software License](https://duckietown.com/sw-license/), [Terms and Conditions](https://duckietown.com/terms-and-conditions/) and [Privacy Policy](https://duckietown.com/privacy/), as well as robot configuration-specific licenses due to the presence of third party software in the SD card. Acceptance is mandatory, resistance is futile.

Start by plugging the SD card into your computer using a SD card reader or the USB to microSD card adapter provided in your Duckiebot kit. Make sure the SD card is detected before proceeding.

2. [Download the Duckietown compressed image](https://cutt.ly/ente-duckiebot-image-207-googledrive) and unzip it

<!--
 temp link above

 ```{todo}
upload image to aws and create redirect from https://duckietown.com/download-duckiebot-ente-image to link
```
-->

The image is downloaded as a compressed `.zip` file. After downloading it to your computer, unzip it to obtain a `.img` file. Flash this file to the SD card (not the `.zip` one).

3. [Install Balena Etcher](https://etcher.balena.io/) or equivalent software

4. Use Balena Etcher to flash the downloaded image to the SD card

Open the Balena Etcher application you just downloaded, and follow the instructions. 

5. Configure the network

Create a network with `ssid` duckietown and passwork `quackquack`, and the Duckiebot will automatically connect to it. 

Alternatively, [edit the Wi-Fi settings on your Duckiebot](duckiebot-setup-wifi) to make it connect to your existing network.

6. Plug in the SD card into your Duckiebot

You are now ready for the [Duckiebot first boot](duckiebot-boot) sequence. 

(db-init-fast-default-settings)=
## Default settings

This image has the following default settings: 

- default username: `duckie`
- default user password: `quackquack`
- robot name (hostname): `entebot`
- type: `duckiebot`
- configuration: `DB21J` (works only with Jetson Nano 4GB developer kit) 
- will connect to Wi-Fi named `duckietown` with password `quackquack`
- country: `US`

(sd-card-flashing-troubleshooting-fast)=
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