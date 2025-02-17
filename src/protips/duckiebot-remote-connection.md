```{seo}
:description: How to connect remotely to a Duckiebot from anywhere in the world using ZeroTier.
:keywords: Duckietown, Duckiebot, remote connection, ZeroTier, VPN, Virtual Private Network
```

(protips-remote-connection)=
# Duckiebot Remote Connection

Have you ever wanted to work from home but your robot is in the lab? 

In this guide, we will show how to access your Duckiebot from anywhere in the world using [ZeroTier](https://www.zerotier.com/). 

ZeroTier is a free, powerful and easy-to-use tool that creates a virtual private network (VPN), allowing devices to communicate as if they were on the same local network, no matter where they are physically located.

We will walk through the following steps:

1. Installing ZeroTier on the Duckiebot
2. Installing ZeroTier on your host computer
3. Creating a ZeroTier network
4. Joining the network from both the Duckiebot and host computer
5. Testing connectivity between your Duckiebot and host computer
6. Running a ROS container using `dts` and accessing the Duckiebot remotely
7. Verifying ROS topic communication

## Step 1: Install ZeroTier on the Duckiebot

To install ZeroTier on your Duckiebot: 

1. SSH into your Duckiebot:
   ```bash
   ssh duckie@<duckiebot_ip_address>
   ```
   
2. Install ZeroTier:
    ```bash
   curl -s https://install.zerotier.com | sudo bash
   ```


## Step 2: Install ZeroTier on Your Host Computer

The host computer is the device used to remotely access your Duckiebot.

To install ZeroTier on your host computer:

`````{tab-set}

````{tab-item} Linux

1. Install ZeroTier:
   ```bash
   curl -s https://install.zerotier.com | sudo bash
   ```

````

````{tab-item} macOS

1. Install ZeroTier via Homebrew:
   ```bash
   brew install zerotier-one
   ```

2. Start the ZeroTier service:
   ```bash
   sudo zerotier-cli join <network_id>
   ```

````

````{tab-item} Windows

1. Download and install ZeroTier from [here](https://www.zerotier.com/download.shtml).
2. Once installed, open the ZeroTier application.

````

`````

<!--
### For Linux:
1. Install ZeroTier:
   ```bash
   curl -s https://install.zerotier.com | sudo bash
   ```

### For macOS:
1. Install ZeroTier via Homebrew:
   ```bash
   brew install zerotier-one
   ```

2. Start the ZeroTier service:
   ```bash
   sudo zerotier-cli join <network_id>
   ```

### For Windows:
1. Download and install ZeroTier from [here](https://www.zerotier.com/download.shtml).
2. Once installed, open the ZeroTier application.
-->

## Step 3: Create a ZeroTier Network

Now that ZeroTier is installed on both your Duckiebot and host computer, the next step is to create a network.

1. Go to the [ZeroTier Central](https://my.zerotier.com/) website and sign up for an account if you do not already have one.
2. Once logged in, click on "Create a Network."
3. Take note of the `network ID` as you will need it in the next steps.

## Step 4: Join the Network

### On the Duckiebot:
1. SSH into your Duckiebot (if not already connected).
2. Join the network using the ZeroTier CLI:
   ```bash
   sudo zerotier-cli join <network_id>
   ```

### On the Host Computer:
1. Open a terminal or the ZeroTier application.
2. Join the network using the ZeroTier CLI or GUI:
   ```bash
   sudo zerotier-cli join <network_id>
   ```

3. Go back to your [ZeroTier Central](https://my.zerotier.com/) and approve the devices that are requesting to join the network by selecting the checkbox next to their address and clicking 'Authorize'. The `Auth` field will turn to a green checkbox ✅.

<!--
   ![Authorize zerotier device](zerotier_authorize_device.png)
-->

```{figure} ../_images/protips/zerotier_authorize_device.png
:width: 400px
:name: Authorizing devices on the ZeroTier virtual network

Authorize your devices on the ZeroTier virtual network.
```


## Step 5: Test Connectivity

To verify that both your Duckiebot and host computer are connected to the ZeroTier network, try pinging your Duckiebot from your host computer:

1. Find the ZeroTier-assigned IP address of your Duckiebot by connecting through ssh and running:
   ```bash
   sudo zerotier-cli info
   ```

   The output will be a string of the type:

   ```bash
   200 info XXXXXXXXXX 1.14.0 ONLINE
   ```

   where `XXXXXXXXXX` will be the IP address assigned to your Duckiebot by ZeroTier.

1. On your host device list the peers and verify that the IP address of your Duckiebot is in the list:

   ```bash
   sudo zerotier-cli listpeers | grep LEAF
   ```
   You can also check the ZeroTier Central dashboard for the IP address.

1. Ping your Duckiebot from your host computer:
   ```bash
   ping <your_duckiebot_name>.local
   ```

If you receive responses, then your Duckiebot and host computer are successfully connected via ZeroTier.

## Step 6: Start a ROS Container Using `dts`

Now that your Duckiebot and host computer are connected, you can start a ROS container on your Duckiebot and interact with it remotely.

1. On your host computer, start the ROS gui tools container:
   ```bash
   dts gui <robot_name>
   ```

   Replace `<robot_name>` with the name of your Duckiebot.

This command will launch a Docker container with ROS, and the GUI will be forwarded to your local machine. You will be connected to the Duckiebot's ROS environment.

## Step 7: Verify ROS Topic Communication

To verify that you're able to listen to ROS topics, use the following commands:

1. List ROS topics:
   ```bash
   rostopic list
   ```

1. Subscribe to a topic (e.g., `<your_robot_name>/camera_node/image/compressed`):
   ```bash
   rostopic echo <your_robot_name>/camera_node/image/compressed
   ```

   If you see the topic data being printed in your terminal, then you have successfully set up remote access to your Duckiebot via ZeroTier.

1. Visualize images (stop the `rostopic echo` by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> ):

   ```bash
   rqt_image_view
   ```
   
   and in the drop-down menu select the `<your_robot_name>/camera_node/image/compressed` topic.

<!--
   <video controls src="zerotier_ros_image.mp4" title="Title"></video>
-->

```{vimeo} 1001988192
:alt: Remote access to a Duckiebot - Running a ROS node to verify connection
```

## Conclusion

By following these steps, you can access your Duckiebot from anywhere in the world using ZeroTier. This setup allows you to interact with your Duckiebot as if it were on your local network, enabling remote development and debugging. 

Whether you are conducting experiments, collecting data, or developing new features, this remote access capability will be precious.