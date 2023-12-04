(request-support)=
# Requesting a Support Connection

(request-support-when)=
## When and why should I run this procedure?

If your Duckiebot ends up in a unique state that is difficult to debug over Slack or other help channels, a Duckietown support engineer may ask you to open a remote support connection.

This connection allows the Duckietown team to take logs from your Duckiebot that will help track down any issues.

The connection will only remain open for as long as you leave the command running.

```{warning}

Because this process enables access to your Duckiebot, you should only follow these steps **when asked by a Duckietown support engineer.**

It is also important to ensure that the connection is closed after taking the logs - you will agree ahead of time on a time to open and complete the support process.

```

## Step 1: Create a request

When instructed to do so, you can create a support request by running

    dts duckiebot support request <your_robot>

This will result in the following message:

```{figure} ../../_images/support-code.png
:name: fig:support-code
```

```{attention}

You will notice that the running process does not exit at this point.  It is important to leave it running in your terminal until instructed to close the support connection.

```

## Step 2: Send the request address

Send the address corresponding to `your_robot.support_address_will_appear_here` in {numref}`fig:support-code` to Duckietown support. They will use this address to retrieve the logs from your Duckiebot.

## Step 3: Close the support connection

Once the debugging process is finished, the Duckietown support engineer will let you know that you can close the connection.

Simply exit the command using `Ctrl^C` in your terminal.
