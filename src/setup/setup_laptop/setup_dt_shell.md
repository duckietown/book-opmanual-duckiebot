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
**1) Install the Duckietown Shell (`dts`)**

Install the Duckietown Shell using the following command,

    pip3 install --no-cache-dir --user --upgrade duckietown-shell


**2) Source `dts`**

Make sure your system can find local binaries by adding the following to your `.bashrc` file. 

```{attention}
If you are using `zsh`, replace the `.bashrc` in the commands below with `.zshrc` instead.
```

    export PATH=~/.local/bin:${PATH}

Then source the updates to your current shell or restart your shell.

    source ~/.bashrc

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

The Duckietown Shell is a [command-line interface (CLI) program](https://en.wikipedia.org/wiki/Command-line_interface) 
that provides all of the necessary Duckietown operations, such as
* Updating a Duckiebot
* Driving a Duckiebot with a virtual keyboard
* Viewing the camera stream of a Duckiebot from a graphical app
* Using our learning experiences
* (and more!)

(laptop-setup-mac-shell)=
**1) Install the Duckietown Shell (`dts`)**

Install the Duckietown Shell using the following command,


    pip3 install --no-cache-dir --user --upgrade duckietown-shell


**2) Source `dts`**

Make sure your system can find local binaries by adding the following to your `.bashrc` file. 

```{attention}
If you are using `zsh`, replace the `.bashrc` in the commands below with `.zshrc` instead.
```

    export PATH=~/.local/bin:${PATH}

Then source the updates to your current shell

    source ~/.bashrc

```{attention}
If this does not work, try using `.bash_profile` and/or `export PATH=~/Library/Python/VERSION/bin:${PATH}` instead, where `VERSION` is your Python version.
```

---

**Checkpoint ✅**

You can now check that `dts` was installed with the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```


````{tab-item} Windows (Beta)

The Duckietown Shell is a [command-line interface (CLI) program](https://en.wikipedia.org/wiki/Command-line_interface) 
that provides all of the necessary Duckietown operations, such as
* Updating a Duckiebot
* Driving a Duckiebot with a virtual keyboard
* Viewing the camera stream of a Duckiebot from a graphical app
* Using our learning experiences
* (and more!)

You can install the Duckietown Shell in your Ubuntu WSL distro.

(laptop-setup-wsl-shell)=
**1) Install the Duckietown Shell (`dts`)**

Install the Duckietown Shell using the following command,

    pip3 install --no-cache-dir --user --upgrade duckietown-shell

Once installed open a new shell and follow the setup prompts.

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
