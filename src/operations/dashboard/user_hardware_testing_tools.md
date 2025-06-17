```{seo}
:description: How to use the Dashboard to test the hardware components on a Duckiebot.
:keywords: Duckietown, Duckiebot, Dashboard, test, hardware components
```
(duckiebot-dashboard-user-hardware-testing-tools)=
# Hardware Component Testing

This section describes how to use the `Dashboard` to test hardware components on your Duckiebot.

```{note}
This section has been designed and tested for the Duckiebot `DB21M`/`DB21J`, and assumes that you have assembled and updated your Duckiebot.
```

(duckiebot-dashboard-user-hardware-testing-tools-where-to-find)=
## Where to find the hardware tests

To open the `Components` tab on the `Robot` page of the `Dashboard`, run:

    dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/components

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122131?h=f69dfe1a26&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 0. where to find"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

(duckiebot-dashboard-user-hardware-testing-tools-demo-videos)=
## Demo videos

Note the components in the table below.

```{list-table}
:header-rows: 1
:name: table-duckiebot-dashboard-user-hardware-testing-tools-test-demos
:widths: 40, 60

* - Component
  - Demo Video
* - Duckiebattery
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
* - Top button
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122268?h=5052dce00d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="howto-9-power-button"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Wi-Fi adapter
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122279?h=bc31caf7bb&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="howto-10-wifi"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Front LEDs
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122292?h=c40771c2f7&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 11. front led"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - Back LEDs
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122305?h=b0e962d075&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 12. back led"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
* - ToF sensor
  - <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/844122323?h=f6cf7d485c&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="HW-Test (v1) How-to: 13. tof"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
```

## Troubleshooting

```{trouble}
When I click the `Test Hardware` button, it does not seem to react and is grayed-out, or the modal shows up but there is no content in it.
---
Make sure that the `duckiebot-interface` container is running by opening the [Portainer interface](dashboard-portainer) or by running:

    `docker -H ![DUCKIEBOT_NAME].local ps`

The exact name of the container will depend on your Duckiebot's version. If you do not see the `duckiebot-interface` container, update your Duckiebot by running:

    `dts duckiebot update ![DUCKIEBOT_NAME]`
```
