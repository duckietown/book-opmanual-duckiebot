(duckiebot-dashboard-user-hardware-testing-tools)=
# Hardware Component Testing

```{note}
This section is designed and tested for DB21-series Duckiebots and onwards.
```

This section shows how to use the Dashboard to test different individual hardware on a Duckiebot.

Assuming you have your Duckiebot assembled, the SD card prepared and the Software updated after booting. Before diving into the beautiful yet could-be-complicated world of robotics and coding, let's do a few simple individual hardware component tests to verify the sensors, actuators, computation and power units work.

The purpose of these tests is to help us be confident in the hardware, and avoid wasting time debugging software without knowing whether the hardware works.

In case you encounter any erroneous behaviors of any of your hardware components, or have any questions about the process, please check out a later sub-section on this page for [FAQs, reporting and getting help](duckiebot-dashboard-user-hardware-testing-tools-getting-help).

(duckiebot-dashboard-user-hardware-testing-tools-where-to-find)=
## Where to find the Hardware Tests

The tests could be accessed on the **Components** tab on the ***ROBOT*** page of the Dashboard.

In each component with the button `Test Hardware`, the test description and expectations would be shown in a **modal** (an on-page pop-up) when the button is clicked. Before running any test, it is recommended to watch the videos in the [next](duckiebot-dashboard-user-hardware-testing-tools-demo-videos) section at least once to see how the robot would behave in each test.

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122131?h=f69dfe1a26&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 0. where to find"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

```{tip}
* You can always perform these tests.
* Later on, if you have problems receiving sensor readings, commanding the motion, or connecting to the robot, maybe you could run these tests again before debugging the code.
```

(duckiebot-dashboard-user-hardware-testing-tools-demo-videos)=
## Demos of the Hardware Tests

These videos would be what you typically need to do or would see, when performing the tests.

(You might want to manually set the video resolution to 1080P, instead of Auto.)

```{list-table}
:header-rows: 1
:name: table-duckiebot-dashboard-user-hardware-testing-tools-test-demos
:widths: 40, 60

* - Component 
  - Demo Video
* - Battery
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122147?h=19640c8604&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 1. battery"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Camera
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122163?h=a62aef34ad&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 2. camera"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Left motor
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122181?h=af78e0ab86&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 3. left motor"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Right motor
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122194?h=735466a0e3&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 4. right motor"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Left encoder
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122205?h=c3a58a438d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 5. left encoder"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Right encoder
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122224?h=0bfeb1de3d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="howto-6-right-encoder"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Screen
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122237?h=464c48f80b&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 7. screen"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - IMU
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122251?h=76a9c2693b&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="howto-8-imu"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Power button
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122268?h=5052dce00d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="howto-9-power-button"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Wifi adapter
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122279?h=bc31caf7bb&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="howto-10-wifi"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Front LEDs
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122292?h=c40771c2f7&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 11. front led"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Back LEDs
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122305?h=b0e962d075&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 12. back led"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Time-of-Flight distance sensor
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122323?h=f6cf7d485c&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 13. tof"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
```

(duckiebot-dashboard-user-hardware-testing-tools-getting-help)=
## FAQs, Reporting Problems & Getting Help

Problems could arise due to faulty hardware, misleading setup instructions, erroneous handling etc. Let's deal with them, patiently and efficiently. This part contains:
* some FAQs
* how to gather logs and enrich the context of an issue reported
* places and formats to post questions and feedback

### FAQs

Here are some common possible issues and resolutions you could already try. If the suggestions do not lead to a successful outcome, do not spend too much time trying it. Maybe we did not make it clear enough. Feel free to report to the team as mentioned in [this part](duckiebot-dashboard-user-hardware-testing-tools-feedback-places-and-formats).

```{trouble}
When I click on the "Test Hardware" button:
* the button does not seem to react / is grayed-out; or
* the modal shows up, but there is no content in it.
---
This is likely because the `duckiebot-interface` container did not start or has not finished initialization successfully. You could go to the "Portainer" page of the Dashboard, and select `Containers` on the left nav-menu. Then, you could try these:
* First, look for the `duckiebot-interface` container, and make sure it exists. If not, try from your host computer: `dts duckiebot update ![ROBOT_NAME]`. After the command finishes, repeat this check in a few minutes.
* If it does exist, check the logs of the container ([Ref: how to check logs in portainer](https://docs.portainer.io/user/docker/containers/logs)). Ask 
```

```{trouble}
Can I close the modal while the test is running?
---
Yes. It will be alive in the background. But you should avoid doing so. Please run only one test at a time, wait until you could check for the expected outcomes, and then close the modal once all done.

When running tests for sensors like camera or ToF, the data would be streamed. It is fine to close the modal after you could determine whether the test passed or failed. On the other hand, for tests with a progress bar, wait for the described time period. Only the LEDs might need a little longer time than written in the description (please check the next FAQ).
```

```{trouble}
My front and back LEDs seem stuck at a color when performing test. Is this normal?
---
The LEDs ideally should be changing brightness or color (or both) all the time during the test. However, it could occur that the frequent commands issued to the LEDs creates a temporary congestion and make the system busy. And the LEDs would appear to be neither changing color nor brightness. The situation should only last for less than 30 seconds.
* Please wait for the duration patiently to see if the test proceeds.
* If it is ever longer than that, please don’t hesitate to contact our team and report the problem.
```

```{trouble}
Would it be harmful if the Duckiebot is turned off during some test runs?
---
No. These are very simple hardware tests. It is perfectly safe to kill any programs or power down the robot.
```

```{trouble}
Why, in the camera test, the image appears smaller than the sensor data size (see `start_gui_tools` in coming sections of this book)?
---
The camera stream in the Dashboard hardware test is resized, such that it fits better in the pop-up modal. The actual data size is always the same as what ROS indicates.
```

### How to provide a rich context when reporting problems
You are of course welcome to ask us your questions directly anytime. In order to get back to you faster and debug efficiently, having richer context would help a lot! That is also why, in the modals you see for each hardware test, there are the buttons for:
* `Download logs of this ROS node`: by clicking this button, a text file will be downloaded from your Duckiebot to your personal computer, containing the logs of the relevant ROS node.
* `Download docker container logs`: by clicking this button, a new modal should pop up, allowing selection of the docker container(s), that is related to this test. The relevant container(s) is/are typically mentioned in the "Logs Gathering" section of the test modal.

```{tip}
Here's a potential example of organizing information in one issue:
1. I am performing **hardware test via the Dashboard** for component: **...**
1. I followed the instructions until this step / am waiting for this outcome: **...**
1. It's not clear what to expect. / The expectation is **...**, but I see **...**
1. The logs for the ROS node: **file/pasted text**
1. The logs for the relevant containers: **file/pasted text**
```

Not only does the rich context help the team recognize the problem and provide solution faster, the community could also benefit, by knowing clearly if someone had an identical/close problem before. And you might be able to find useful answers just by searching our StackOverflow.

In the next sub-section, we recommend some tags and endpoints for communicating the issues to.

(duckiebot-dashboard-user-hardware-testing-tools-feedback-places-and-formats)=
### Where to post questions & feedback

* **(Preferred)** [StackOverflow for Duckietown](https://stackoverflowteams.com/c/duckietown/questions)
  * It is recommended to use these tags when posting on StackOverflow
    * `robot-setup`
    * `hwtest`, `hw tests`, `hardware-test`, `hardware-tests` (and other similar)
    * `hwtest-`***Name of the component***
* You could also ask on the Duckietown Slack, on the `help-robot-setup` channel. But it is more preferable to post technical issues on our StackOverflow, and any other feedback on Slack.
  * Here are some kinds of "_any other feedback_":
    * The tests ran but the description clarity could improve **here and here**.
    * The test design would be better if the content is **this**.
