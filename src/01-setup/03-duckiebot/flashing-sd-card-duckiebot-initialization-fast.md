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
- An initialized SD card for your Duckiebot with default configuration settings.
```

(setup-db-sd-card-flashing-fast)=
# The Fast Way - Initialization

Use this procedure if you want a quicker result, and do not mind having [default settings](db-init-fast-default-settings).

```{tip}
Robots on the same network must have unique names. **Do not follow this procedure if you plan on having multiple Duckiebots on the same network.**
```

```{attention}
By proceeding with these instructions you are accepting the [Duckietown terms of use](initialization-tos). 
```

<!--
Internal note: current ente image version 2.0.8
When creating a new image:
0. Use robotname: entebot+[version number], e.g., `entebot208`
1. Upload to AWS public / images S3 bucket
2. Upload to (Shared) Duckiebot Images GDrive 
3. Create trackable links with Cuttly
4. Update redirects on Cloudflare > duckietown.com > Rules
5. update robot name in "default settings" paragraph below
-->

(initialize-sd-card-video-fast)=
## Duckiebot (`DB21J`) image download

1. Read and understand the [](initialization-tos) before proceeding. For any questions or doubts, [reach out](mailto:info@duckietown.com).

2. Download the Duckietown compressed image:
    * [Download non-customizable `DB21J` Duckiebot `ente` image from AWS](https://duckietown.com/download-duckiebot-ente-sdcard-image-aws)  
    * [Download non-customizable `DB21J` Duckiebot `ente` image from Google Drive](https://duckietown.com/download-duckiebot-ente-sdcard-image-googledrive)

    The image is downloaded as a compressed `.zip` file. Programs like Balena Etcher allow flashing this format directly to the SD card. If you are using a different program, unzip the downloaded file to obtain a `.img` file to flash to the SD card.

3. [Install Balena Etcher](https://etcher.balena.io/) or equivalent software

4. Use Balena Etcher to flash the downloaded image to the SD card

    Open the Balena Etcher application you just downloaded, and follow the 3 steps instructions (select the file, select the sd card, press start).

5. Configure the network on the Duckiebot

    This image is pre-configured to so that the Duckiebot will connects to a network with SSID `duckietown` and password `quackquack`.

    To have the Duckiebot connect to a different network, your will have to [edit the Wi-Fi settings on your Duckiebot](setup-duckiebot-edit-networks).

    To access the `/etc/wpa_supplicant.conf` file on your Duckiebot, choose one of these options:

    * If you have an Ubuntu computer set up: plug the SD card of the Duckiebot in your computer through the provided SD card adapter, navigate to the `/media/duckietown/[...]/etc/` folder, [edit the Wi-Fi settings](setup-duckiebot-network) with `sudo nano wpa_supplicant.conf`; or,

    * if you do not have an Ubuntu computer set up: create a temporary hotspot with your phone, windows or macOS computer with SSID `duckietown` and WPA-PSK password `quackquack`, and connect your computer to it. Plug the SD card in the Duckiebot, and after the [first boot](duckiebot-boot), which will take a few minutes, the Duckiebot will connect to it. It does not matter at this stage having internet connection, so you can disconnect the data plan if using a phone. From your computer the [SSH into the Duckiebot](handling-how-to-ssh-into-your-duckiebot), and proceed to [edit the Wi-Fi settings](setup-duckiebot-network). Or,

    * if you have access to the router and an ethernet cable, connect your Duckiebot through the ethernet cable to the router, connect your computer to the same network, and proceed to [SSH into the Duckiebot](handling-how-to-ssh-into-your-duckiebot) to [edit the Wi-Fi settings](setup-duckiebot-network).

6. Plug in the SD card into your Duckiebot (if not already done).

7. Perform the [Duckiebot first boot](duckiebot-boot) sequence (if not already done).

(db-init-fast-default-settings)=
## Default settings

This image has the following default settings:

- default username: `duckie`
- default user password: `quackquack`
- robot name (hostname): `entebot208`
- type: `duckiebot`
- configuration: `DB21J` (works only with Jetson Nano 4GB developer kit) 
- will connect to Wi-Fi named `duckietown` with password `quackquack`
- country: `US`

For additional information on the meaning of these parameters, see: [](setup-db-sd-card-flashing-complete).


(initialization-tos)=
### Legal things - Accepting Duckietown legal terms

By downloading this image you accept the [Duckietown Software License](https://duckietown.com/sw-license/), [Terms and Conditions](https://duckietown.com/terms-and-conditions/) and [Privacy Policy](https://duckietown.com/privacy/), as well as robot configuration-specific licenses due to the presence of third party software in the SD card. Acceptance is mandatory, resistance is futile.

Start by plugging the SD card into your computer using a SD card reader or the USB to microSD card adapter provided in your Duckiebot kit. Make sure the SD card is detected before proceeding.


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