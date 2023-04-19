## Step 1: Duckietown Account Setup

(dt-account-dockerhub-shell-credentials)=
### 1) Configure the Duckietown Shell

The first thing you need to do with `dts` is to set the Duckietown software distribution you want to work with.
For this version of the book, we use daffy. Set the shell to use the daffy distribution by running the following command

    dts --set-version daffy

(dt-account-register)=
### 2) Get a Duckietown Token

Now your Duckietown Shell needs a Duckietown token. The Duckietown Token allows you to authenticate yourself and your robots against the Duckietown network.

You can make a Duckietown account for free from the Duckietown Website.
[Make an account here!](https://hub.duckietown.com/)

The token is a string of letters and numbers that looks something like this:

    dt1-7vEuJsaxeXXXXX-43dzqWFnWd8KBa1yev1g3UKnzVxZkkTbfSJnxzuJjWaANeMf4y6XSXBWTpJ7vWXXXX

To find your token, first [log in](https://hub.duckietown.com/) to your account, 
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

```{testexpect}
If the Duckietown Shell was installed correctly, then you can run a command like this
```bash
dts version
---
Verify that the commands version is set to `daffy`.
```

```{testexpect}
Check if your token was successfully by running
```bash
dts tok status
---
This should output a message like the following,
```bash
dts :  Correctly identified as uid = ***
```

If you have encountered issues or something is not behaving as expected, please stop here,
it is a good time to ask for help on Stack Overflow.

You can join the 
[Duckietown community on Slack at this link](https://join.slack.com/t/duckietown/shared_invite/enQtNTU0Njk4NzU2NTY1LWM2YzdlNmJmOTg4MzAyODc2YTI3YTc5MzE2MThkZGUwYTFkZWQ4M2ZlZGU1YTZhYjg5YTgzNDkyMzI2ZjNhZWE). 
There you can request an invitation to the Duckietown Stack Overflow team.




