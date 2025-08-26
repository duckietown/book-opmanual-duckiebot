(duckiebot-dashboard-setup)=
# Setup - Duckiebot Dashboard

```{seo}
:description: Tep by step instructions on how to set up your Duckiebot Dashboard in Duckietown.
:keywords: Duckietown, Duckiebot, Dashboard, Compose, browser based UI
```

```{needget}
- A Duckietown account: [](setup-account-duckietown-hub)
- A connected Duckiebot: [](setup-duckiebot-network)
---
- A working Duckiebot Dashboard for hardware and software diagnostics
```

This section shows how to install a perform the first setup of the Duckietown Dashboard on the Duckiebot.

<!--
(compose-platform)=
## The \compose\ platform

\\compose\\ is a CMS (Content Management System) platform that provides functionalities
for fast-developing web applications. Custom applications are developed as external
packages that can be installed using the built-in Package Store.

The Duckiebot Dashboard is a package that you can install on your instance
of \\compose\\ running on your Duckiebot.
To make it easier for you to get started, we provide a Docker image with \\compose\\
and all the packages you need already running on your Duckiebot after the first boot. Follow the instructions in the next step to get started.
-->

(init-dashboard)=
## Setting up the Duckiebot Dashboard

The Dashboard comes pre-installed on your Duckiebot, and gets activated on first boot. A one-time procedure is necessary to set it up before it being ready for use.

Once configured, you can connect to the Dashboard through _any_ browser by going to `http://ROBOT_NAME.local/`.

(init-dashboard-video)=
### Video Tutorial

````{admonition} How to set up a Duckietown Duckiebot Dashboard

```{vimeo} 526989336
:alt: How to set up a Duckietown Duckiebot Dashboard
```
Dashboard setup tutorial.
````

<!--
```{admonition} How to set up a Duckietown Duckiebot Dashboard
<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/526989336" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
<p>Dashboard setup tutorial.</p>
```

<div figure-id="fig:howto-dashboard-setup" figure-caption="Dashboard setup tutorial.">
    <dtvideo src="vimeo:526989336"/>
</div>
-->
(init-dashboard-steps)=
### Step-by-Step Instructions

You can find your duckietown Dashboard at:

    http://ROBOT_NAME.local/

If the above address does not work, remove the `.local` part and just use 

    http://ROBOT_NAME/

```{note}
If `.local` does not work, that means your router's default domain name is set to something else. It will be helpful if you figure out what that is. And keep in mind that any instruction later that includes `.local` should be just ignored.
```

You will be greeted by the Dashboard shown here. Read the steps below before continuing through the setup page.

```{figure} ../../_images/setup/dashboard/compose_first_setup_step3.png
:alt: duckietown dashboard first configuration splash screen
:width: 75%
:name:  compose_first_setup
:align: center
```

#### Steps 1 and 2: Login and administrator account

To authenticate your account on the Dashboard, use your personal Duckietown token.

You will notice that the first two steps in the Dashboard already appear to be completed.

Do not worry about configuring Google sign-in (Step 1) or creating an administrator account (Step 2) for now,
a new administrator account will be automatically created.

#### Step 3: Configure your Dashboard

Complete the `Configure \compose\` fields and click on **Next** to continue.

```{note}
You can always update your choices through the **Settings** page after you finish the setup process.
```

```{tip}
If you are seeing an error due to permissions, take a look at the [Booting FAQs](boot-faq).
```

#### Step 4: Complete the setup

The **Step 4: Complete** tab should now be open, as shown below.

```{figure} ../../_images/setup/dashboard/compose_first_setup_step4.png
:name: compose_first_setup_step4
:alt: duckietown dashboard completing first configuration
:width: 75%
:name:  compose_first_setup_completion
:align: center
```

Press **Finish** to continue.

### Dashboard First Login

You should now see the login page:

```{figure} ../../_images/setup/dashboard/dashboard_login_page.png
:name: dashboard_login_page
:alt: duckietown dashboard login page
:width: 75%
:align: center
```

```{note}
Since your Dashboard does not have an administrator account yet, the first user to login will be automatically assigned the role of
administrator. If you have multiple tokens, make sure to keep note of which one you used for the first login.
```

If you have not retrieved your personal Duckietown Token as described in [](duckietown-token) yet, it is now time to do so. 

Once you have your token click on **Sign in with Duckietown**.

```{figure} ../../_images/setup/dashboard/dashboard_login_with_duckietown_modal.png
:name: dashboard_login_with_duckietown_modal
:alt: duckietown dashboard sign in with duckietown widget
:width: 75%
:align: center
```

If your token is active, you will be redirected to your profile page:

```{figure} ../../_images/setup/dashboard/dashboard_profile_page_full.png
:name: dashboard_profile_page
:alt: duckietown dashboard profile page
:width: 75%
:align: center
```

The left side bar shows many more pages, some immediately available, others under development. Some pages are accessible by all users (e.g., Robot), others only by administrators (e.g., Settings, Package Store).

Take your time to visit all the pages and get comfortable with the Duckiebot Dashboard. A deeper dive on each page is available at [](sw-tools-ui-dashboard).
