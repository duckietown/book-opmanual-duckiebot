# Image Viewer

```{seo}
:description: The Image Viewer.
:keywords: Duckietown, Duckiebot, Image Viewer
```

<<<<<<< HEAD
<<<<<<< Updated upstream
(image-viewer)=
# Image Viewer

This chapter describes the `Image Viewer`.

```{needget}
Completed [](dtps).
---
Knowledge on the `Image Viewer`.
```

=======
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
This chapter describes the `Image Viewer`.

```{needget}
Completed [](dtps.md).
---
Knowledge on the `Image Viewer`.
```

<<<<<<< HEAD
>>>>>>> Stashed changes
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
## Introduction

One of the easiest ways to see what your Duckiebot sees is by using the `Image Viewer`.

```{figure} ../_images/software_tools/image_viewer/image_viewer.png
The `Image Viewer`.
```

To open the `Image Viewer`, run:

```shell
dts duckiebot image_viewer DUCKIEBOT_NAME
```

Note the keys in the table below.

```{list-table}
:header-rows: 1
:name: table:image-viewer-commands

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

(operation-make-it-see-troubleshooting)=
## Troubleshooting

```{trouble}
<<<<<<< HEAD
<<<<<<< Updated upstream
I can see messages being sent from my Duckiebot when looking at the `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](dtps), but I do not see an image.
=======
I can see messages being sent from my Duckiebot when looking at the `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](dtps.md), but I do not see an image.
>>>>>>> Stashed changes
=======
I can see messages being sent from my Duckiebot when looking at the `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](dtps.md), but I do not see an image.
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
---
Make sure that the `duckiebot-interface` container is running by checking the `Portainer` page of the `Dashboard` (opened by running `dts duckiebot dashboard DUCKIEBOT_NAME --page portainer`) or by running:

    `docker -H DUCKIEBOT_NAME.local ps`

The exact name of the container will depend on your Duckiebot's version. If you do not see the `duckiebot-interface` container, update your Duckiebot by running:

    `dts duckiebot update DUCKIEBOT_NAME`
```

```{trouble}
<<<<<<< HEAD
<<<<<<< Updated upstream
I cannot see an image after refreshing the window and I cannot see messages being sent from my Duckiebot when looking at the `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](dtps).
=======
I cannot see an image after refreshing the window and I cannot see messages being sent from my Duckiebot when looking at the `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](dtps.md).
>>>>>>> Stashed changes
=======
I cannot see an image after refreshing the window and I cannot see messages being sent from my Duckiebot when looking at the `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg` `DTPS` topic, after following [](dtps.md).
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
---
Contact support.
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
