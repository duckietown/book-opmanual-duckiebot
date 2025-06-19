```{seo}
:description: How to view the DTPS topics on a Duckiebot.
:keywords: Duckietown, Duckiebot, DTPS
```

(operation-view-dtps-topics)=
# Operation - View DTPS Topics

This section describes how to view the DTPS (Duckietown Postal Service) topics on your Duckiebot.

```{figure} ../../_images/operations/dtps_html_interface.png
:name: dtps-html-interface

The DTPS HTML interface for a Duckiebot named "duckiebot".
```

To view the DTPS topics on your Duckiebot, run:

    dts duckiebot dtps ![DUCKIEBOT_NAME]

To view a specific DTPS topic on your Duckiebot, run the following command, where `![TOPIC]` is the topic (e.g., `![DUCKIEBOT_NAME]/sensor/camera/front_center/jpeg`):

    dts duckiebot dtps ![DUCKIEBOT_NAME] --topic ![TOPIC]

```{figure} ../../_images/operations/dtps_jpeg_topic.png
:name: dtps-jpeg-topic

The `![DUCKIEBOT_NAME]/sensor/camera/front_center/jpeg` DTPS topic HTML interface for a Duckiebot named "duckiebot".
```
