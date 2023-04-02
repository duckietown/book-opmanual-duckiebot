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


## Verify everything is correct

Before we move on, let us make sure you have installed everything correctly.

If some of these commands don’t work, please go back and fix it before continuing.

If the Docker installation went well, then you can run the following command:

    $ docker run hello-world
    Hello from Docker!
    This message shows that your installation appears to be working correctly.

If you set up a Github account and private key, you should be able to run this command successfully:

    $ ssh -T git@github.com
    Hi GITHUB_USERNAME! You've successfully authenticated, but GitHub does not provide shell access.

If you have a valid DockerHub account then you can login as follows.

    $ docker login -u DOCKER_USERNAME
    Password:

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
