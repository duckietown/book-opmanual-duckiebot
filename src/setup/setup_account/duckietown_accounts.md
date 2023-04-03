## Step 1: Duckietown Account Setup

```{todo}
This is a collection of all prev. dts setup info, needs to be sorted into steps
```

(dt-account-dockerhub-shell-credentials)=
### Configure the Duckietown Shell

The [Duckietown Challenges Server](https://challenges.duckietown.org) allows you to participate in robotics
competitions, submit class homeworks, etc., by uploading your work, packaged as a Docker image, to DockerHub.

Use the following command to give your DockerHub credentials to the Duckietown Shell so that your work
can be seamlessly uploaded to DockerHub on your behalf and for the Duckietown Challenges Server to 
evaluate your work on the cloud.

    dts challenges config --docker-username USERNAME --docker-password PASSWORD

where, `USERNAME` and `PASSWORD` need to be replaced with your DockerHub credentials.

(dt-account-register)=
# Get a Duckietown Token

You can make a Duckietown account for free from the Duckietown Website. 
[Make an account now!](https://www.duckietown.org/site/register).


(dt-account-find-token)=
# Retrieve your Duckietown token

The Duckietown Token allows you to authenticate yourself and your robots against the Duckietown network.

The token is a string of letters and numbers that looks something like this:

    dt1-7vEuJsaxeXXXXX-43dzqWFnWd8KBa1yev1g3UKnzVxZkkTbfSJnxzuJjWaANeMf4y6XSXBWTpJ7vWXXXX

To find your token, first [log in](https://www.duckietown.org/pm_login) to your account, 
then open [this page](https://www.duckietown.org/site/your-token) in your browser:

```{note}
It may take up to 5 minutes after signing up for a token to be generated.
```


(dt-account-set-token)=
# Tell the Duckietown Shell your token

You can tell the Duckietown Shell who you are by running the command below and following the 
instructions presented,

    dts tok set

Verify your token was successfully set by running the shell command,

    dts tok status

You should see a message like the following,

    dts :  Correctly identified as uid = ***


# Setup the Duckietown Shell



# `dts` versions and login's

Your `dts` is further setup in this section.

## Use the latest stable distribution version
```bash
dts --set-version daffy
```


## Set your Duckietown token
You could obtain your token by logging in on the [Duckietown homepage](https://duckietown.com). Then token looks like: `dt1-xxx`.

To add the token to `dts`, run the following command,
```bash
dts tok set YOUR_DUCKIETOWN_TOKEN
```

You can verify you successfully authenticated using the Duckietown token by running the command,
```bash
dts tok status
```

The expected output looks like the following,
```text
dts :  Correctly identified as uid = [YOUR_DUCKIETOWN_USER_ID]
```


If the Duckietown Shell was installed, then you can run a command like this,

    dts version

If you correctly configured the token, then the command below should show something similar to the following,

    $ dts challenges info
    ~        You are successfully authenticated:
    ~
    ~                     ID: YOUR ID
    ~                   name: YOUR NAME
    ~                  login: YOUR DUCKIETOWN ACCOUNT 
    ~
    ~         You can find the list of your submissions at the page:
    ~
    ~              https://challenges.duckietown.org/v4/humans/users/YOUR ID

If you have encountered issues or something is not working or behaving as expected, please stop here,
it is a good time to ask for help on Stack Overflow.

The first thing you need to do with the Duckietown Shell, is set the Duckietown software
distribution you want to work with, for this version of the book, we use `daffy`.
Set the shell to use the `daffy` distribution by running the following command,

    dts --set-version daffy
