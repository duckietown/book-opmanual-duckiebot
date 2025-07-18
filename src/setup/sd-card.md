<<<<<<< HEAD
<<<<<<< Updated upstream
=======
# SD Card

>>>>>>> Stashed changes
=======
# SD Card

>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
```{seo}
:description: How to initialize an SD card for a Duckiebot.
:keywords: Duckietown, Duckiebot, initialize, SD card
```

<<<<<<< HEAD
<<<<<<< Updated upstream
(sd-card)=
# SD Card

This chapter describes how to initialize an SD card for your Duckiebot.

```{needget}
* Completed [](computer).
=======
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
This chapter describes how to initialize an SD card for your Duckiebot.

```{needget}
* Completed [](computer/dts.md).
<<<<<<< HEAD
>>>>>>> Stashed changes
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
* An SD card with at least `64 GB` of space.
* An SD card adapter.
---
An initialized SD card for your Duckiebot.
```

```{note}
If you are using a microSD to SD card adapter, make sure that the adapter does not have write protection enabled.
```

(chose-robot-hostname)=
## Setup

Plug the SD card into your computer using an SD card reader or the USB to microSD card adapter provided in your Duckiebot kit.

Choose a hostname for your Duckiebot, such that it:

* Is unique within a fleet of Duckiebots connected to the same network.
* Is fully lowercase.
* Starts with a letter.
* Contains only letters, numbers and underscores.

(initialize-sd-card)=
## Initialization

```{vimeo} 526698325
```

To begin the SD card initialization procedure using the CLI, run the following command, where `HOSTNAME` is the hostname of your Duckiebot, `CONFIGURATION` is its configuration (e.g., DB21J), `WIFI` is a comma-separated list of Wi-Fi networks of the form `NETWORK_NAME:NETWORK_PASSWORD`, where `NETWORK_NAME` and `NETWORK_PASSWORD` are the network name and password, respectively, and `COUNTRY` is the optional country code (e.g., US):

```shell
dts init_sd_card --hostname HOSTNAME --type duckiebot --configuration CONFIGURATION --wifi WIFI [--country COUNTRY]
```

```{note}
Each network defined in `WIFI` can support the following arguments:

* Open networks (`SSID`).
* PSK (Pre-Shared Key) protected networks (`SSID:PSK`).
* EAP (Extensible Authentication Protocol) protected networks (`SSID:USERNAME:PASSWORD`).
```

(sd-card-flashing-troubleshooting)=
## Troubleshooting

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
