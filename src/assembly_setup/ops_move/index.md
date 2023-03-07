(rc-control)=
# Operation - Make it Move

This section describes how to make your Duckiebot move.

```{tip}
If any one of the following commands does not work for you, see the **Troubleshooting** section at the end of this page.  **Troubleshooting** sections are provided at the end of each operation page - start there if you run into any issues.
```

(make-it-move_shell)=
## Keyboard control

The easiest way to move a Duckiebot is by using the `keyboard_control` command provided in the Duckietown shell. This video shows how to drive a Duckiebot using the keyboard, through the Duckietown Shell.

<div figure-id="fig:howto-virtual" figure-caption="Duckiebot keyboard control.">
<dtvideo src="vimeo:526584868"/>
</div>

### Option 1: Use the GUI (For Linux Users)

If you are using Mac OSX, [see Option 2](mac-users-cli). 

To move your Duckiebot using your computer's keyboard open a terminal and run:

    dts duckiebot keyboard_control ![DUCKIEBOT_NAME]

```{attention}
For all operation commands that use the Duckiebot's name - replace `![DUCKIEBOT_NAME]` with just the Duckiebot's `hostname`, do not include `.local` part that you used previously to access the dashboard.
```

After startup, the `keyboard_control` command will open an interface window. Make sure the window is active by selecting it, and use the keys in the table below to command your Duckiebot:

```{figure} ../../_images/assembly_setup/setup_dashboard/keyboard_gui.png
:name: keyboard_control_gui

The keyboard control graphical user interface.
```

The following keys control the Duckiebot:

```{list-table}
:header-rows: 1
:name: keyboard-control-commands

* - KEY
  - Function
* - Arrow Keys - <kbd>&uarr;</kbd> <kbd>&darr;</kbd> <kbd>&larr;</kbd> <kbd>&rarr;</kbd>
  - Steer your Duckiebot
* - <kbd>q</kbd>
  - Quit
* - <kbd>a</kbd>
  - Turn on lane following (see note below)
* - <kbd>s</kbd>
  - Stop lane following
* - <kbd>i</kbd>
  - Toggle Anti-Instagram
```

```{note}
The <kbd>a</kbd>, <kbd>s</kbd>, and <kbd>i</kbd> functions require the [lane following demo](demo-lane-following) to be running. For now, just try out the keyboard control and get your Duckiebot moving!
```

(mac-users-cli)=
### Option 2: Use the CLI (For Mac Users)

If you are using MacOSX and find the keyboard interface is not responsive, run the stack directly on the Duckiebot and use the same keys within the command line interface as listed in the [table above](keyboard-control-commands):

    dts duckiebot keyboard_control ![DUCKIEBOT_NAME] --cli

## Troubleshooting

```{trouble}
The Duckiebot does not move, and I cannot see the commands being sent to the Duckiebot when looking at the **Dashboard > Mission Control** page.
---
Make sure that the keyboard gui window is active by selecting it, then try the keyboard commands again.  Some keyboard configurations may require that you use <kbd>w</kbd> <kbd>a</kbd> <kbd>s</kbd> <kbd>d</kbd> rather than <kbd>&uarr;</kbd> <kbd>&darr;</kbd> <kbd>&larr;</kbd> <kbd>&rarr;</kbd>.
```

```{trouble}
I can see the commands being sent to the Duckiebot (e.g., through the **Dashboard > Mission Control**), but the Duckiebot does not move. My **Dashboard > Robot > Components** page shows a red alert for the `HUT`.
---
If you have a `HUT` v3.15 you will stumble on this problem the first time you try to move your Duckiebot. Re-flash your `HUT` following the procedure described in [](reflash-microcontroller).
```

```{trouble}
I checked the two troubleshooting issues above, and my Duckiebot still doesn't move.
---
Check that the `duckiebot-interface` container is running

Open [the Portainer interface](dashboard-portainer) and check the running containers. You should see one that has a name that contains `duckiebot-interface` (exact container name will depend on your robot version).

You can also determine this by running:

    `docker -H ![ROBOT_NAME].local ps`

and look at the output to find the `duckiebot-interface` container and verify that it is running.

If you don't see the container, your base image is out of date - update your Duckiebot with the command

    `dts duckiebot update ![ROBOT_NAME]`
```

```{trouble}
Symptom: Duckiebot goes backwards, even though I command it to go forward.
---
Resolution: If you have a `DB17` or `DB18`, revert the polarities (plus and minus cables) of the cables that go to the motor driver (`HUT`) for both motors.
```
