(db-troubleshooting-hut)=
# HUT

```{seo}
:description: How to re-flash a HUT's microcontroller.
:keywords: Duckietown, Duckiebot, re-flash, HUT, microcontroller
```

This chapter describes how to re-flash the HUT's microcontroller.

```{needget}
Completed [](sw-tools-ui-dashboard).
---
Knowledge on how to re-flash the HUT's microcontroller.
```

```{attention}
This procedure is only required if your Duckiebot does not recognize the HUT, which can be seen on the `Components` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components`).
Although often unnecessary, it is safe to perform this procedure on any HUT v2.0 or newer.
```

## Introduction

This procedure re-flashes the HUT's microcontroller.
This microcontroller is responsible for translating the duty cycle commands from the on-board computer to PWM signals that control your Duckiebot's motors and LEDs (because they are *addressable* LEDs).
This is often necessary if, for example, your Duckiebot does not move, even though commands are being sent to its motors.

```{note}
This procedure will not be useful if only one motor works or the LEDs show unexpected colors but the motors work.
```

## Using DTS

To re-flash the HUT's microcontroller, run:

```shell
dts duckiebot hut_upgrade DUCKIEBOT_NAME
```

## Using SSH

Run the following command and enter the password if required (the default password is `quackquack`):

```shell
ssh duckie@DUCKIEBOT_NAME.local
```

Run:

```shell
sudo apt-get update
sudo apt-get install bison autoconf flex gcc-avr binutils-avr gdb-avr avr-libc avrdude build-essential
git clone https://github.com/duckietown/fw-device-hut.git
cd fw-device-hut
```

```{caution}
Read the following instructions carefully.
```

If your Duckiebot has an NVIDIA Jetson Nano, run:

```shell
sudo cp _avrdudeconfig_jetson_nano/avrdude.conf /etc/avrdude.conf
```

Otherwise, if your Duckiebot has a Raspberry Pi, run:

```shell
sudo cp _avrdudeconfig_raspberry_pi/avrdude.conf /etc/avrdude.conf
```

Run:

```shell
make fuses
```

````{warning}
If the resulting output does not look like the following, **do not continue**:

```shell
...
avrdude: AVR device initialized and ready to accept instructions
avrdude: device signature = 0x1e930d (probably t861)
avrdude: reading input file 0xe2 for lfuse
        with 1 byte in 1 section within [0, 0]
avrdude: writing 1 byte lfuse ...
avrdude: 1 byte of lfuse written
avrdude: verifying lfuse memory against 0xe2
avrdude: 1 byte of lfuse verified
avrdude: reading input file 0xdf for hfuse
        with 1 byte in 1 section within [0, 0]
avrdude: writing 1 byte hfuse ...
avrdude: 1 byte of hfuse written
avrdude: verifying hfuse memory against 0xdf
avrdude: 1 byte of hfuse verified
avrdude: reading input file 0xff for efuse
        with 1 byte in 1 section within [0, 0]
avrdude: writing 1 byte efuse ...
avrdude: 1 byte of efuse written
avrdude: verifying efuse memory against 0xff
avrdude: 1 byte of efuse verified

avrdude done.  Thank you.
```
````

Run:

```shell
make clean
make
```

````{note}
The resulting output should look similar to the following:

```shell
...
avrdude: AVR device initialized and ready to accept instructions
avrdude: device signature = 0x1e930d (probably t861)
avrdude: Note: flash memory has been specified, an erase cycle will be performed.
        To disable this feature, specify the -D option.
avrdude: erasing chip
avrdude: reading input file main.hex for flash
        with 2782 bytes in 1 section within [0, 0xadd]
        using 44 pages and 34 pad bytes
avrdude: writing 2782 bytes flash ...

Writing | ################################################## | 100% 1.23 s

avrdude: 2782 bytes of flash written
avrdude: verifying flash memory against main.hex

Reading | ################################################## | 100% 0.86 s

avrdude: 2782 bytes of flash verified

avrdude done.  Thank you.
```
````

Run:

```shell
cd .. && rm -rf fw-device-hut
sudo reboot
```

Once your Duckiebot has rebooted, run the following command and check if the HUT is detected:

```shell
dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components
```
