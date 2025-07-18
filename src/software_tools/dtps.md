<<<<<<< HEAD
<<<<<<< Updated upstream
=======
# DTPS

>>>>>>> Stashed changes
=======
# DTPS

>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
```{seo}
:description: DTPS (Duckietown Postal Service).
:keywords: Duckietown, Duckiebot, DTPS, Duckietown Postal Service
```

<<<<<<< HEAD
<<<<<<< Updated upstream
(dtps)=
# DTPS

This chapter describes `DTPS` (`Duckietown Postal Service`).

```{needget}
Completed [](dashboard).
=======
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
This chapter describes `DTPS` (`Duckietown Postal Service`).

```{needget}
Completed [](dashboard.md).
<<<<<<< HEAD
>>>>>>> Stashed changes
=======
>>>>>>> ente-DTSW-6848-Update-book-opmanual-duckiebot
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
