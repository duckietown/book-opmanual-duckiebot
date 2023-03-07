(duckiebot-dashboard-setup)=
# Setup - Dashboard

This section shows how to install the Duckietown Dashboard on the Duckiebot.

(compose-platform)=
## The \compose\ platform

\\compose\\ is a CMS (Content Management System) platform that provides functionalities
for fast-developing web applications. Custom applications are developed as external
packages that can be installed using the built-in Package Store.

The Duckiebot Dashboard is a package that you can install on your instance
of \\compose\\ running on your Duckiebot.
To make is easier for you to get started, we provide a Docker image with \\compose\\
and all the packages you need. Follow the instructions in the next step to get started.

Visit the
[official documentation page](http://compose.afdaniele.com/docs/latest/index)
for further information.

(init-dashboard)=
## Setting up dashboard

(init-dashboard-video)=
### Video Tutorial

<div figure-id="fig:howto-dashboard-setup" figure-caption="Dashboard setup tutorial.">
    <dtvideo src="vimeo:526989336"/>
</div>

(init-dashboard-steps)=
### Step-by-Step Instructions

You can find your duckietown dashboard at:

    http://![YOUR_DUCKIEBOT_NAME].local/

If the above address does not work, remove the `.local` part and just use 

    http://![YOUR_DUCKIEBOT_NAME]/

```{note}
If `.local` does not work, that means your router's default domain name is set to something else. It will be helpful if you figure out what that is. And keep in mind that any instruction later that includes `.local` should be just ignored.
```

You should be greeted by the dashboard shown here. Read the steps below before continuing through the setup page.

```{figure} ../../_images/assembly_setup/setup_dashboard/compose_first_setup_step3.png
:name: compose_first_setup
```

#### Steps 1 and 2: Already done!

By default, \\compose\\ uses Google Sign-In to authenticate the users.  In Duckietown, we use authentication based on personal tokens.

You will notice that the first two steps in the dashboard already appear to be completed.
Do not worry about configuring Google sign-in (Step 1) or creating an administrator account (Step 2) for now,
a new administrator account will be automatically created the first time we log in
using a Duckietown token later on.

#### Step 3: Configure your dashboard

```{figure} ../../_images/assembly_setup/setup_dashboard/compose_first_setup_step3.png
:name: compose_first_setup_step3
```

You can complete these fields as you please.

```{note}
You can always update your choices through the **Settings** page after you finsh the setup process.
```

When you are happy with your choices, click on **Next**.

#### Step 4: Complete the setup

The **Step 4: Complete** tab should now be open, as shown below.

```{figure} ../../_images/assembly_setup/setup_dashboard/compose_first_setup_step4.png
:name: compose_first_setup_step4
```

You can go ahead and press **Finish**.

### First Login

If everything went as planned, the dashboard is now configured and ready to go!

You should be able to see the login page, as shown below.

```{figure} ../../_images/assembly_setup/setup_dashboard/dashboard_login_page.png
:name: dashboard_login_page
```

```{note}
Since your dashboard does not have an administrator account yet,
the first user to login will be automatically assigned the role of
administrator. If you have multiple tokens, make sure to keep note of
which one you used for the first login.
``` 

If you have not retrieved your personal Duckietown Token as described in [](dt-account) yet,
it is now time to do so. You should be able to
retrieve your token by visiting the page here:

> [`https://www.duckietown.org/site/your-token`](https://www.duckietown.org/site/your-token)

Once you have your personal Duckietown token, go ahead and click on
the button **Sign in with Duckietown**.

```{figure} ../../_images/assembly_setup/setup_dashboard/dashboard_login_with_duckietown_modal.png
:name: dashboard_login_with_duckietown_modal
```

Copy/paste or type in your personal token and press Login.
Wait for the token to be validated, and if your token is correct, you will
be redirected to your profile page, similar to the one shown below.

```{figure} ../../_images/assembly_setup/setup_dashboard/dashboard_profile_page_full.png
:name: dashboard_profile_page
```

As you might have noticed, the side bar to the left now shows many more pages. Some pages are
accessible by all users (e.g., Robot), others only by administrators (e.g., Settings,
Package Store).

Take your time to visit all the pages and get comfortable with the platform.
We will discuss the functionalities offered by each page in the next sections.
