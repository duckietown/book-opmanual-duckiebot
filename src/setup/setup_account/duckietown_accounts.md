```{seo}
:description: You will require several accounts with (free) third-party software to use Duckietown. Here is a ste-by-step guide on how to set up your accounts.
:keywords: Duckietown, setup, accounts
```

## Step 1: Duckietown Account Setup

(dt-account-dockerhub-shell-credentials)=
### 1) Configure the Duckietown Shell

The first thing you need to do with `dts` is to set the Duckietown software distribution you want to work with.
For this version of the book, we use daffy. Set the shell to use a profile on the daffy distribution by running the command

    dts profile switch daffy

(dt-account-register)=
### 2) Get a Duckietown Token

Now your Duckietown Shell needs a Duckietown token. The Duckietown Token allows you to authenticate yourself and your robots against the Duckietown network.

You can make a Duckietown account for free from the Duckietown Hub.
[Make an account here.](https://hub.duckietown.com/signup/)

The token is a string of letters and numbers that looks something like this:

    dt1-7vEuJsaxeXXXXX-43dzqWFnWd8KBa1yev1g3UKnzVxZkkTbfSJnxzuJjWaANeMf4y6XSXBWTpJ7vWXXXX

To find your token, first [log in](https://hub.duckietown.com/signin/) to your account, 
then open [the profile page](https://hub.duckietown.com/profile/) in your browser:

Copy your token to use in the next step.

(dt-account-set-token)=
### 3) Set your token in the Duckietown Shell

You can tell the Duckietown Shell who you are by running the command below and following the 
instructions presented in the shell

    dts tok set

---

### Checkpoint ✅

Run the following tests to check your setup:

````{testexpect}
If the Duckietown Shell was installed correctly, then you can run a command like this
   ```bash
   dts version
   ```
---
Verify that the version of the commands is set to `daffy`.
````

````{testexpect}
Check if your token was successfully by running
   ```bash
   dts tok status
   ```
---
This should output a message like the following,
   ```bash
   dts :  Correctly identified as uid = ***
   ```
````

If you have encountered issues or something is not behaving as expected, please stop here, it is a good time to ask for help on Stack Overflow.

````{trouble}
(For OSX) DuckieTown shell fails to install dependencies and throws errors similar to:

   ```none
   error: subprocess-exited-with-error
   × Getting requirements to build wheel did not run successfully.
   exit code: 1
   ╰─> See above for output.

   note: This error originates from a subprocess, and is likely not a problem with pip.
---
DuckieTown shell dependencies are dictated by the <code>requirements.txt</code> file located at

<pre>~/.duckietown/shell/profiles/daffy/commands/duckietown/__command_set__/requirements.txt</pre>

<p>Open the `requirements.txt` file and compare each dependency to your installed packages via</p>

<pre><code>pip3 freeze</code></pre>

OR

<pre><code>pip3 freeze | grep [PACKAGE NAME]</code></pre>

Version differences may be the culprit, especially if the original error is related to pyYAML.
Forcing pip to install DuckieTown specific package versions (e.g. `pip3 install --user pyyaml==5.4.1`) may resolve the issue.

:::{warning}
Forcing package upgrade/downgrades outside of a virtual environment may break other application dependencies.
:::
````

You can join the 
[Duckietown community on Slack at this link](https://duckietown.com/join-slack). 

There you can request an invitation to the Duckietown Stack Overflow, by following [these instructions](https://duckietown.slack.com/archives/CHHQJ0E0H/p1670874390660429).


