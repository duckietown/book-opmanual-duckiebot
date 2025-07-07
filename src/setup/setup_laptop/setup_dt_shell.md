```{seo}
:description: The Duckietown Shell (dts) is a command line interface that abstracts many of the nitty-gritty details of daily operations in Duckietown. Here is an installation guide to dts.
:keywords: Duckietown, setup, laptop, DTS, Duckietown shell, installation, how to install the duckietown shell
```

(laptop-setup-shell)=
# Step 3: Duckietown Shell Installation

`````{tab-set}

````{tab-item} Ubuntu

The Duckietown Shell is a [command-line interface (CLI) program](https://en.wikipedia.org/wiki/Command-line_interface) 
that provides all of the necessary Duckietown operations, such as
* Updating a Duckiebot
* Driving a Duckiebot with a virtual keyboard
* Viewing the camera stream of a Duckiebot from a graphical app
* Using our learning experiences
* (and more!)

(laptop-setup-ubuntu-shell)=
**Install the Duckietown Shell (`dts`)**

Install the Duckietown Shell using the following command:

    pipx install duckietown-shell

---

**Checkpoint ✅**

To confirm that `dts` was installed successfully, run the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```

````


````{tab-item} macOS

```{warning}
This configuration is not officially supported. We recommend using the Ubuntu Operating System for an optimal experience.
```

The Duckietown Shell is a [command-line interface (CLI) program](https://en.wikipedia.org/wiki/Command-line_interface) 
that provides all of the necessary Duckietown operations, such as
* Updating a Duckiebot
* Driving a Duckiebot with a virtual keyboard
* Viewing the camera stream of a Duckiebot from a graphical app
* Using our learning experiences
* (and more!)

(laptop-setup-mac-shell)=
**Install the Duckietown Shell (`dts`)**

Install the Duckietown Shell using the following command:

    pipx install duckietown-shell

---

**Checkpoint ✅**

You can now check that `dts` was installed with the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```


````{tab-item} Windows

```{warning}
This configuration is not officially supported. We recommend using the Ubuntu Operating System for an optimal experience.
```

The Duckietown Shell is a [command-line interface (CLI) program](https://en.wikipedia.org/wiki/Command-line_interface) 
that provides all of the necessary Duckietown operations, such as
* Updating a Duckiebot
* Driving a Duckiebot with a virtual keyboard
* Viewing the camera stream of a Duckiebot from a graphical app
* Using our learning experiences
* (and more!)

You can install the Duckietown Shell in your Ubuntu WSL distro.

(laptop-setup-wsl-shell)=
**Install the Duckietown Shell (`dts`)**

Install the Duckietown Shell using the following command:

    pipx install duckietown-shell

---
**Checkpoint ✅**

To confirm that dts was installed successfully, run the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```

````
`````
