(protip-zerotier-remote-duckiebot-control)=
# Remote Duckiebot control with ZeroTier

```{seo}
:description: How to connect to a Duckiebot over the Internet using ZeroTier.
:keywords: Duckietown, Duckiebot, connect, ZeroTier
```

This chapter describes how to connect to your Duckiebot over the Internet using ZeroTier.

```{needget}
* Completed [](how-to-handle-a-duckiebot-db21).
* A [ZeroTier account](https://my.zerotier.com/).
---
Knowledge on how to connect to your Duckiebot over the Internet using ZeroTier.
```

## Introduction

[ZeroTier](https://www.zerotier.com/) is a free, powerful and easy-to-use tool that creates a VPN (Virtual Private Network), allowing devices to communicate as if they were on the same local network, no matter where they are physically located.

## Installation

To install ZeroTier on your computer and Duckiebot, run the following command on both:

```shell
curl -s https://install.zerotier.com | sudo bash
```

## Creating a ZeroTier network

To create a ZeroTier network:

1. Navigate to [ZeroTier Central](https://my.zerotier.com/).
2. Log in if you are not already logged in.
3. Click the `Create a Network` button (note the `network ID`).

## Creating connection requests

To create a connection request for your computer and Duckiebot, run the following command on both, where `NETWORK_ID` is the `network ID`:

```shell
sudo zerotier-cli join NETWORK_ID
```

## Approving connection requests

To approve connection requests:

1. Navigate to [ZeroTier Central](https://my.zerotier.com/).
2. Log in if you are not already logged in.
3. Select the addresses of your computer and Duckiebot.
4. Click the `Authorize` button.

```{figure} ../_images/further_reading/zerotier/zerotier_authorize_device.png
ZeroTier device authorization.
```

## Checkpoint

````{testexpect}
On your Duckiebot, run:

```shell
sudo zerotier-cli info
---
The following output, where `XXXXXXXXXX` is the IP address assigned to your Duckiebot by ZeroTier:

```shell
200 info XXXXXXXXXX 1.14.0 ONLINE
````

````{testexpect}
On your computer, run:

```shell
sudo zerotier-cli listpeers | grep LEAF
---
A list containing the IP address assigned to your Duckiebot by ZeroTier.
````

````{testexpect}
On your computer, run:

```shell
ping DUCKIEBOT_NAME.local
```
---
Responses from your Duckiebot.
````
