(db-testing-hw-components)=
# Testing - Duckiebot Hardware Components

```{seo}
:description: How to test hardware components on a Duckiebot using the Duckietown Dashboard
:keywords: Duckietown, Duckiebot, Dashboard, test, hardware components
```

```{needget}
- A booted Duckiebot: [](duckiebot-boot)
---
- A correctly assembled Duckiebot
```

## Introduction

To open the `Components` tab on the `Robot` page of the `Dashboard`, run:

```shell
dts duckiebot dashboard DUCKIEBOT_NAME --page robot/components
```

```{vimeo} 844122131?h=f69dfe1a26&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
```

(duckiebot-dashboard-user-hardware-testing-tools-demo-videos)=
## Demonstration videos

Note the components in the table below.

```{list-table}
:header-rows: 1
:name: table:duckiebot-dashboard-user-hardware-testing-tools-test-demos
:widths: 40, 60

* - Component
  - Demonstration Video
* - Duckiebattery
  - ```{vimeo} 844122147?h=19640c8604&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Camera
  - ```{vimeo} 844122163?h=a62aef34ad&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Left motor
  - ```{vimeo} 844122181?h=af78e0ab86&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Right motor
  - ```{vimeo} 844122194?h=735466a0e3&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Left encoder
  - ```{vimeo} 844122205?h=c3a58a438d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Right encoder
  - ```{vimeo} 844122224?h=0bfeb1de3d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Screen
  - ```{vimeo} 844122237?h=464c48f80b&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - IMU
  - ```{vimeo} 844122251?h=76a9c2693b&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Top button
  - ```{vimeo} 844122268?h=5052dce00d&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Wi-Fi adapter
  - ```{vimeo} 844122279?h=bc31caf7bb&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Front LEDs
  - ```{vimeo} 844122292?h=c40771c2f7&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - Back LEDs
  - ```{vimeo} 844122305?h=b0e962d075&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
* - ToF sensor
  - ```{vimeo} 844122323?h=f6cf7d485c&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479
    ```
```

## Troubleshooting

```{trouble}
When I click the `Test Hardware` button, it does not seem to react and is grayed-out, or the modal shows up but there is no content in it.
---
Make sure that the `duckiebot-interface` container is running by checking the `Portainer` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page portainer`) or by running:

    `docker -H DUCKIEBOT_NAME.local ps`

The exact name of the container will depend on your Duckiebot's version. If you do not see the `duckiebot-interface` container, update your Duckiebot by running:

    `dts duckiebot update DUCKIEBOT_NAME`
```
