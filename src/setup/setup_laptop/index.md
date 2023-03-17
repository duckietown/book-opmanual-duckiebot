(laptop-setup)=
# Setup - Laptop

This chapter will cover the laptop setup.


## Minimal Laptop Requirements

These installation steps make sure that you have a minimal "sane" environment, which includes:

1. Git;
2. Docker;
3. The Duckietown Shell;


## Native installation vs virtual machines

Having Ubuntu installed natively on your laptop is recommended but not strictly required.

If you are running Ubuntu in a VM make sure that you are using a Bridged network adapter
(for example VirtualBox uses NAT by default). This allows you to be on the same subnetwork
as your Duckiebot.

Sometimes when running a VMware machine on a Mac OS host, it is neccessary to have two
network adapters: _Share with my Mac_ for connecting to the internet and _Bridged Networking_
for connecting to the Duckiebot.

For more information about networking with VMware, see [here](https://wiki.ros.org/ROS/NetworkSetup).