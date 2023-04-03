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

The first thing you need to do with the Duckietown Shell, is set the Duckietown software
distribution you want to work with, for this version of the book, we use `daffy`.
Set the shell to use the `daffy` distribution by running the following command,

    dts --set-version daffy
    
**✅ Checkpoint**
```{todo}```


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
Again, if you are using `zsh`, replace the `.bashrc` in the commands below with `.zshrc` instead.
```

    export PATH=~/.local/bin:${PATH}

Then source the updates to your current shell

    source ~/.bashrc

You can now check that `dts` was installed with 

    which dts

The first thing you need to do with the Duckietown Shell is to set the Duckietown software
distribution you want to work with. For this version of the book, we use `daffy`.
Set the shell to use the `daffy` distribution by running the following command,

    dts --set-version daffy

**✅ Checkpoint**
```{todo}```


````

`````