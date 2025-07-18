# Network

```{seo}
:description: How to connect a Duckiebot to a network.
:keywords: Duckietown, Duckiebot, network
```

This chapter describes how to connect your Duckiebot to a network.

```{needget}
Completed [](../setup/sd-card.md).
---
Knowledge on how to connect your Duckiebot to a network.
```

## Using Wi-Fi

To edit the Wi-Fi networks known to your Duckiebot, edit the `wpa_supplicant.conf` file in the main partition of the SD card.
If your Duckiebot has an NVIDIA Jetson Nano, this file is located in the `/etc` directory in the `APP` partition.
Otherwise, if your Duckiebot has a Raspberry Pi, this file is located in the `/etc/wpa_supplicant` directory in the `root` partition.

````{note}
The following is from a `wpa_supplicant.conf` file with two Wi-Fi networks defined:

```shell
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=CH

network={
    id_str="network_1"
    ssid="comnet23243"
    psk="MSNDJWKE32"
    key_mgmt=WPA-PSK
}

network={
    id_str="network_2"
    ssid="TPlink23432"
    psk="ksnbn4wn3"
    key_mgmt=WPA-PSK
}
```
````

## Using Ethernet

```{note}
This method assumes that you can connect your computer to a network that is out of your control or is not open (e.g., one that is protected using [PEAP](https://en.wikipedia.org/wiki/Protected_Extensible_Authentication_Protocol)).
```

To connect your Duckiebot to a network through your computer:

1. Connect your computer to the network.
2. Connect your Duckiebot to your computer using an Ethernet cable.
3. Navigate to `Network Connections` (run `sudo nm-connection-editor`).
4. Click the `+` (`Add a new connection`) button.
5. Select the `Ethernet` option from the drop-down menu.
6. Click the `Create...` button.
7. Enter a `Connection name` (e.g., "Duckiebot connection").
8. Click the `IPv4 Settings` button.
9. Select the `Shared to other computers` option from the `Method` drop-down menu.
10. Click the `Save` button.

(duckiebot-network-test)=
## Test your Duckiebot's connection to the Internet

Run the following command and enter the password (the default password is `quackquack`):

```shell
ssh duckie@DUCKIEBOT_NAME.local
```

Run:

```shell
ping duckietown.com
```

````{note}
Over time, the resulting output should look similar to the following:

```shell
PING duckietown.com (172.67.205.80) 56(84) bytes of data.
64 bytes from 172.67.205.80 (172.67.205.80): icmp_seq=1 ttl=53 time=26.4 ms
64 bytes from 172.67.205.80 (172.67.205.80): icmp_seq=2 ttl=53 time=24.9 ms
64 bytes from 172.67.205.80 (172.67.205.80): icmp_seq=3 ttl=53 time=27.4 ms
64 bytes from 172.67.205.80 (172.67.205.80): icmp_seq=4 ttl=53 time=24.0 ms
64 bytes from 172.67.205.80 (172.67.205.80): icmp_seq=5 ttl=53 time=24.5 ms
...
```
````

## Troubleshooting

```{trouble}
I cannot ping my Duckiebot (`ping DUCKIEBOT_NAME` does not work) over Wi-Fi.
---
Make sure that the contents of the `wpa_supplicant.conf` file are correct.
```

```{trouble}
The contents of the `wpa_supplicant.conf` file are correct and I can ping my Duckiebot over Ethernet but not over Wi-Fi.
---
If you have control over the network access point, make sure that both your computer and Duckiebot are connected to the network.
```

```{trouble}
Running `ssh duckie@DUCKIEBOT_NAME.local` results in the following output:

    `ssh: Could not resolve hostname DUCKIEBOT_NAME.local: Name or service not known`
---
After connecting your Duckiebot to a monitor and keyboard, run:

    `sudo systemctl restart avahi-daemon`

Run:

    `sudo reboot`
```

```{trouble}
Running `ssh duckie@DUCKIEBOT_NAME.local` still results in the following output:

    `ssh: Could not resolve hostname DUCKIEBOT_NAME.local: Name or service not known`
---
After connecting your Duckiebot to a monitor and keyboard, run:

    `sudo service avahi-daemon status`

The resulting output should look similar to the following:

`
    ● avahi-daemon.service - Avahi mDNS/DNS-SD Stack
       Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
       Active: active (running) since Fri 2025-06-20 04:17:36 CDT; 2h 20min ago
     Main PID: 3814 (avahi-daemon)
       Status: "avahi-daemon 0.7 starting up."
        Tasks: 2 (limit: 4183)
       CGroup: /system.slice/avahi-daemon.service
            ├─3814 avahi-daemon: running [DUCKIEBOT_NAME_IN_AVAHI.local]
            └─4000 avahi-daemon: chroot helper
`

If `DUCKIEBOT_NAME_IN_AVAHI` matches `DUCKIEBOT_NAME-XX`, where `XX` is a number, edit the `/etc/avahi/avahi-daemon.conf` file by changing `use-ipv6=yes` to `use-ipv6=no` and `#publish-aaaa-on-ipv4=yes` to `publish-aaaa-on-ipv4=no`.

Run:

   `sudo service avahi-daemon restart`
```
