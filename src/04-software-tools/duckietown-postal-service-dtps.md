(sw-tools-dtps)=
# Duckietown Postal Service (`DTPS`)

```{seo}
:description: DTPS (Duckietown Postal Service).
:keywords: Duckietown, Duckiebot, DTPS, Duckietown Postal Service
```

This chapter describes `DTPS` (`Duckietown Postal Service`).

```{needget}
Completed [](sw-tools-ui-dashboard).
---
Knowledge on `DTPS`.
```

## Introduction

`DTPS` is an HTTP/2 compatible message-passing system.

## HTML interface

```{figure} ../_images/software_tools/dtps/dtps_html_interface.png
The `DTPS` HTML interface for a Duckiebot named "duckiebot".
```

To open the main `DTPS` HTML interface for your Duckiebot, run the following command, where `TOPIC` is an optional topic (e.g., `DUCKIEBOT_NAME/sensor/camera/front_center/jpeg`):

```shell
dts duckiebot dtps [--topic TOPIC] DUCKIEBOT_NAME
```

### KV store

The KV (Key-Value) store is a database for your Duckiebot, where data is stored as a collection of key-value pairs.

To open the KV store `DTPS` HTML interface for your Duckiebot, run the following command, where `TOPIC` is an optional topic (e.g., `data/robot/type`):

```shell
dts duckiebot dtps --kv_store [--topic TOPIC] DUCKIEBOT_NAME
```
