(setup-db-sd-card-flashing-intro)=
# Duckiebot SD Card preparation - introduction

```{seo}
:description: Instructions on how to flash an SD card to initialize a Duckiebot, Duckiedrone, Traffic Light or Watchtower.
:keywords: Duckietown, Duckiebot, Duckiedrone, flashing, initialization, SD card, Traffic Light, Watchtower, dts init sd card, dts init_sd_card
```

```{needget}
* An SD card with at least `64 GB` of space.
* An SD card adapter appropriate for the computer you are using to flash the SD card
* A broadband internet connection
* 20 - 40 mins, depending on internet connection speed and procedure (easy/complete)
* At least 40 GB of free space on your hard drive before starting
* [Functional DTS installation](setup-dts) if using the [Complete - Initialization](setup-db-sd-card-flashing-complete) procedure.
---
An initialized SD card for your Duckiebot with customized settings. 
```


While the hardware represents the body of the robot, the software running on it is its mind. In this chapter we set up the mind of the Duckiebot. 

In other words, we initialize an SD card for Duckietown robots, e.g., a Duckiebot, by flashing a Duckietown image on an SD card, the hard drive of the robot.

We provide two approaches two procedures to do so:

1. ["The Fast Way"](setup-db-sd-card-flashing-fast): requires less time, can be performed with any operating system, does not need to have the Duckietown Shell installed, but allows for no customization of the robot name. Recommended for testing of a single robot.  
2. ["The Complete Way"](setup-db-sd-card-flashing-complete): requires a functional [Duckietown Shell installation](setup-dts), takes roughly twice the time of the faster approach, but allows for full customization. Recommended when operating more than one Duckiebot. 