```{seo}
:description: How to access the Duckiebot camera stream (or, see what it sees).
:keywords: Duckietown, Duckiebot, camera stream, perception, image sensing
```

(operation-make-it-see)=
# Operation - Make it See

This section describes how to see what your Duckiebot sees.

(operation-make-it-see-image-viewer)=
## The Image Viewer

One of the easiest ways to see what your Duckiebot sees is by using the `Image Viewer`.

```{figure} ../../_images/operations/image_viewer.png
:name: image-viewer

The `Image Viewer`.
```

To activate the `Image Viewer`, run:

    dts duckiebot image_viewer ![DUCKIEBOT_NAME]

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: image-viewer-commands

* - Key
  - Function
* - <kbd>X</kbd>
  - Increase the `Frame Rate`
* - <kbd>Z</kbd>
  - Decrease the `Frame Rate`
* - <kbd>Space</kbd>
  - Capture an image
* - <kbd>R</kbd>
  - Refresh the window
* - <kbd>T</kbd>
  - Open the `Debug Console`
```

(operation-make-it-see-dashboard)=
## Dashboard

Another easy way to see what your Duckiebot sees is by using the `Dashboard`.

To see what your Duckiebot sees through the `Dashboard`, run:

    dts duckiebot dashboard ![DUCKIEBOT_NAME] --page robot/mission_control

(operation-make-it-see-troubleshooting)=
## Troubleshooting

```{trouble}
I do not see an image after refreshing the window and I cannot see messages being sent from my Duckiebot when looking at the `![DUCKIEBOT_NAME]/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](operation-view-dtps-topics).
---
Contact support.
```

```{trouble}
I can see messages being sent from my Duckiebot when looking at the `![DUCKIEBOT_NAME]/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](operation-view-dtps-topics), but I do not see an image.
---
Make sure that the `duckiebot-interface` container is running by opening the [Portainer interface](dashboard-portainer) or by running:

    `docker -H ![DUCKIEBOT_NAME].local ps`

The exact name of the container will depend on your Duckiebot's version. If you do not see the `duckiebot-interface` container, update your Duckiebot by running:

    `dts duckiebot update ![DUCKIEBOT_NAME]`
```

```{trouble}
I see a black image.
---
Make sure that the protective cap for your Duckiebot's camera lens has been removed.
```

```{trouble}
The images are out of focus.
---
The focus for your Duckiebot's camera can be manually adjusted by rotating the mechanical focus ring on the lens. When dealing with hardware, exercise care and minimize the use of force. Occasionally, cameras come with the lens glued in place. If the lens does not rotate, you may need to break the glue.
```
