(laptop-setup-shell)=
## Step 3: Duckietown Shell Installation

`````{tab-set}

````{tab-item} Ubuntu

The Duckietown Shell is a [command-line interface (CLI) prgram](https://en.wikipedia.org/wiki/Command-line_interface) 
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

---

**Checkpoint ✅**

To confirm that dts was isntalled successfully, run the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```

````


````{tab-item} MacOSX

The Duckietown Shell is a [command-line interface (CLI) prgram](https://en.wikipedia.org/wiki/Command-line_interface) 
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


**2) Source dts**

Make sure your system is able to find local binaries by adding the following to your `.bashrc` file. 

```{attention}
If you are using `zsh`, replace the `.bashrc` in the commands below with `.zshrc` instead.
```

    export PATH=~/.local/bin:${PATH}

Then source the updates to your current shell

    source ~/.bashrc

---

**Checkpoint ✅**

You can now check that `dts` was installed with the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```

`````

````{tab-item} Windows (Beta)

The Duckietown Shell is a [command-line interface (CLI) prgram](https://en.wikipedia.org/wiki/Command-line_interface) 
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

Once installed open a new shell and run

    dts --set-version daffy
---

**Checkpoint ✅**

To confirm that dts was isntalled successfully, run the following test

```{testexpect}
```bash
which dts
---
This should output a path ending in `dts`.
```

````
