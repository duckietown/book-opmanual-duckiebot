```{seo}
:description: Professional software development typically leverages versioning to keep track of changes. Git is a powerful tool to collaborate on sophisticated projects, and GitHub is a typical interface.
:keywords: Duckietown, Duckiebot, software, software development, Git, GitHub, robotics projects
```

(version_control_with_git)=
# Version Control with Git

Professional software development typically leverages versioning to keep track of changes. [Git](https://git-scm.com/) is a powerful tool to collaborate on sophisticated projects, and [GitHub](https://github.com/) provides a convenient interface.

<div figure-id="fig:tutorial-git-video" figure-caption="An introduction to version control with Git.">
    <dtvideo src="vimeo:526923344"/>
</div>

## Background reading

See: [Github tutorial](https://guides.github.com/activities/hello-world/)

See: [Github workflow](https://guides.github.com/introduction/Llow/)

## Installation

The basic Git program is installed using

    sudo apt install git

Additional utilities for `git` are installed using:

    sudo apt install git-extras

This includes the `git-ignore` utility, which comes in handy when you have files that you do not
actually want to push to the remote branch (such as temporary files).


(howto-git-local-config)=
##Setting up global configurations for Git

Use these commands to tell Git who you are:

    git config --global user.email "![email]"
    git config --global user.name  "![full name]"


## Git tips

### Fork a repository

To fork (creating a copy of a repository, that does not belong to you), you simply have to go
to the repository's webpage dashboard and click fork on the upper right corner.

### Clone a repository

To clone a repository, copy either the HTTPS or SSH link from the repository's webpage.
The following command will download the git repository in a new directory on the local computer
(starting from the current working directory).

    git clone git@github.com:USERNAME/REPOSITORY

If you have SSH setup properly, you can directly download it.
If you are using the HTTPS then github will ask for your credentials.

### Move between branches

You can move to a different branch using the command,

    git checkout ![destination-branch]


### Create a new branch

After you successfully cloned a repository, you may want to work on your own branch.
Move to the branch you want to start from and run the following command,

    git checkout -b ![branch-name]

To see which branch you are working on you can either use both of these commands

    git branch
    git status

The latter provides more information on which files you might have changed, which are staged
for a new commit or that you are up-to-date (everything is ok).

### Commit and Push changes

After you edited some files, you want to push your changes from the local to the remote location.
Check the changes that need to be committed/pushed with the command,

    git status

Use the following command to mark a `![file]` as ready to be committed,

    git add ![file]

Once you marked all the files you want to include in the next commit, complete the commit with
a commit message to let collaborators know what you have changed,

    git commit -m "![commit-message]"

If everything went well, you are now ready to push your changes to your remote with,

    git push origin ![branch-name]


### Fetch new branches

If new branches have been pushed recently to the repository and you don't have them you can invoke a

    git fetch --all

to see all new branches and checkout to those.

### Delete branches

To delete a local branch execute (you cannot be on the branch that you are going to delete!):

    git branch -d ![branch-name]

To delete a remote branch you need to push the delete command:

    git push origin --delete ![branch-name]

### Open a pull request

If you are working on another branch than the master or if you forked a repository and want to propose changes you made into the master, you can open a so-called `pull-request`. In order to do so, press the corresponding tab in the dashboard of a repository and then press the green button `New pull request`. You will be asked which branch from which fork you want to merge.

### Keep your password stored locally

If you are setting up Github on your own personal computer, and you use two factor authentication, it might be time consuming to configure that every time you need to provide git credentials. Instead, you can have the computer to remember your password. To do that, you can:

    git config --global credential.helper store

Please note you should only do that if this is your personal computer!

## Connect with SSH

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys#about-ssh-keys):

You can use SSH to perform Git operations in repositories on GitHub.com.

If you have an existing SSH key, you can use the key to authenticate Git operations over SSH.

### Checking for existing SSH keys

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys#checking-for-existing-ssh-keys):

`````{tab-set}
````{tab-item} Ubuntu
Before you generate a new SSH key, you should check your local machine for existing keys.

1. Open Terminal.

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present.
    ```
    $ ls -al ~/.ssh
    # Lists the files in your .ssh directory, if they exist
    ```

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.
    * `id_rsa.pub`
    * `id_ecdsa.pub`
    * `id_ed25519.pub`
    ```{tip}
    If you receive an error that `~/.ssh` doesn't exist, you do not have an existing SSH key pair in the default location. You can create a new SSH key pair in the next step.
    ```

4. Either generate a new SSH key or upload an existing key.
    * If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
    * If you see an existing public and private key pair listed (for example, `id_rsa.pub` and `id_rsa`) that you would like to use to connect to GitHub, you can add the key to the ssh-agent.
````

````{tab-item} macOS
Before you generate a new SSH key, you should check your local machine for existing keys.

1. Open Terminal.

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present.
    ```
    $ ls -al ~/.ssh
    # Lists the files in your .ssh directory, if they exist
    ```

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.
    * `id_rsa.pub`
    * `id_ecdsa.pub`
    * `id_ed25519.pub`
    ```{tip}
    If you receive an error that `~/.ssh` doesn't exist, you do not have an existing SSH key pair in the default location. You can create a new SSH key pair in the next step.
    ```

4. Either generate a new SSH key or upload an existing key.
    * If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
    * If you see an existing public and private key pair listed (for example, `id_rsa.pub` and `id_rsa`) that you would like to use to connect to GitHub, you can add the key to the ssh-agent.
````

````{tab-item} Windows
Before you generate a new SSH key, you should check your local machine for existing keys.

1. Open Git Bash.

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present.
    ```
    $ ls -al ~/.ssh
    # Lists the files in your .ssh directory, if they exist
    ```

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.
    * `id_rsa.pub`
    * `id_ecdsa.pub`
    * `id_ed25519.pub`
    ```{tip}
    If you receive an error that `~/.ssh` doesn't exist, you do not have an existing SSH key pair in the default location. You can create a new SSH key pair in the next step.
    ```

4. Either generate a new SSH key or upload an existing key.
    * If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
    * If you see an existing public and private key pair listed (for example, `id_rsa.pub` and `id_rsa`) that you would like to use to connect to GitHub, you can add the key to the ssh-agent.
````
`````

### Generating a new SSH key

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key):

``````{tab-set}
`````{tab-item} Ubuntu
You can generate a new SSH key on your local machine. After you generate the key, you can add the public key to your account on GitHub.com to enable authentication for Git operations over SSH.

1. Open Terminal.

2. Paste the text below, replacing the email used in the example with your GitHub email address.
    ```
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```
    ````{note}
    If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```
    ````
    This creates a new SSH key, using the provided email as a label.
    ```
    > Generating public/private ALGORITHM key pair.
    ```
    When you're prompted to "Enter a file in which to save the key", you can press `Enter` to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace `id_ALGORITHM` with your custom key name.
    ```
    > Enter a file in which to save the key (/home/YOU/.ssh/id_ALGORITHM):[Press enter]
    ```

3. At the prompt, type a secure passphrase.
    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```
`````

`````{tab-item} macOS
You can generate a new SSH key on your local machine. After you generate the key, you can add the public key to your account on GitHub.com to enable authentication for Git operations over SSH.

1. Open Terminal.

2. Paste the text below, replacing the email used in the example with your GitHub email address.
    ```
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```
    ````{note}
    If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```
    ````
    This creates a new SSH key, using the provided email as a label.
    ```
    > Generating public/private ALGORITHM key pair.
    ```
    When you're prompted to "Enter a file in which to save the key", you can press `Enter` to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace `id_ALGORITHM` with your custom key name.
    ```
    > Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM):[Press enter]
    ```

3. At the prompt, type a secure passphrase.
    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```
`````

`````{tab-item} Windows
You can generate a new SSH key on your local machine. After you generate the key, you can add the public key to your account on GitHub.com to enable authentication for Git operations over SSH.

1. Open Git Bash.

2. Paste the text below, replacing the email used in the example with your GitHub email address.
    ```
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```
    ````{note}
    If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```
    ````
    This creates a new SSH key, using the provided email as a label.
    ```
    > Generating public/private ALGORITHM key pair.
    ```
    When you're prompted to "Enter a file in which to save the key", you can press `Enter` to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace `id_ALGORITHM` with your custom key name.
    ```
    > Enter file in which to save the key (c:\Users\YOU\.ssh\id_ALGORITHM):[Press enter]
    ```

3. At the prompt, type a secure passphrase.
    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```
`````
``````

### Adding your SSH key to the SSH agent

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent):

``````{tab-set}
````{tab-item} Ubuntu
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. 

1. Start the ssh-agent in the background.
    ```
    $ eval "$(ssh-agent -s)"
    > Agent pid 59566
    ```
    Depending on your environment, you may need to use a different command. For example, you may need to use root access by running `sudo -s -H` before starting the ssh-agent, or you may need to use `exec ssh-agent bash` or `exec ssh-agent zsh` to run the ssh-agent.

2. Add your SSH private key to the ssh-agent.

    If you created your key with a different name, or if you are adding an existing key that has a different name, replace `id_ed25519` in the command with the name of your private key file.
    ```
    ssh-add ~/.ssh/id_ed25519
    ```

3. Add the SSH public key to your account on GitHub.
````

`````{tab-item} macOS
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS `ssh-add` command, and not an application installed by [macports](https://www.macports.org/), [homebrew](https://brew.sh/), or some other external source.

1. Start the ssh-agent in the background.
    ```
    $ eval "$(ssh-agent -s)"
    > Agent pid 59566
    ```
    Depending on your environment, you may need to use a different command. For example, you may need to use root access by running `sudo -s -H` before starting the ssh-agent, or you may need to use `exec ssh-agent bash` or `exec ssh-agent zsh` to run the ssh-agent.

2. If you're using macOS Sierra 10.12.2 or later, you will need to modify your `~/.ssh/config` file to automatically load keys into the ssh-agent and store passphrases in your keychain.

    * First, check to see if your `~/.ssh/config` file exists in the default location.
    ```
    $ open ~/.ssh/config
    > The file /Users/YOU/.ssh/config does not exist.
    ```
    * If the file doesn't exist, create the file.
    ```
    touch ~/.ssh/config
    ```
    * Open your `~/.ssh/config` file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
    ```
    Host github.com
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_ed25519
    ```
    ````{note}
    * If you chose not to add a passphrase to your key, you should omit the `UseKeychain` line.
    * If you see a `Bad configuration option: usekeychain` error, add an additional line to the configuration's' `Host *.github.com` section.
    ```
    Host github.com
      IgnoreUnknown UseKeychain
    ```
    ````

3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace `id_ed25519` in the command with the name of your private key file.
    ```
    ssh-add --apple-use-keychain ~/.ssh/id_ed25519
    ```
    ```{note}
    The `--apple-use-keychain` option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the `--apple-use-keychain` option.

    The `--apple-use-keychain` option is in Apple's standard version of `ssh-add`. In macOS versions prior to Monterey (12.0), the `--apple-use-keychain` and `--apple-load-keychain` flags used the syntax `-K` and `-A`, respectively.

    If you don't have Apple's standard version of `ssh-add` installed, you may receive an error.

    If you continue to be prompted for your passphrase, you may need to add the command to your `~/.zshrc` file (or your `~/.bashrc` file for bash).
    ```

4. Add the SSH public key to your account on GitHub.
`````

````{tab-item} Windows
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. 

If you have [GitHub Desktop](https://desktop.github.com/) installed, you can use it to clone repositories and not deal with SSH keys.

1. In a new `admin elevated` PowerShell window, ensure the ssh-agent is running.
    ```
    # start the ssh-agent in the background
    Get-Service -Name ssh-agent | Set-Service -StartupType Manual
    Start-Service ssh-agent
    ```

2. In a terminal window without elevated permissions, add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace `id_ed25519` in the command with the name of your private key file.
    ```
    ssh-add c:\Users\YOU\.ssh\id_ed25519
    ```

3. Add the SSH public key to your account on GitHub.
````
``````

### Generating a new SSH key for a hardware security key

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key-for-a-hardware-security-key):

``````{tab-set}
`````{tab-item} Ubuntu
If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key.

1. Insert your hardware security key into your computer.

2. Open Terminal.

3. Paste the text below, replacing the email address in the example with the email address associated with your account on GitHub.
    ```
    ssh-keygen -t ed25519-sk -C "your_email@example.com"
    ```
    ````{note}
    If the command fails and you receive the error `invalid format` or `feature not supported`, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
    ```
    ssh-keygen -t ecdsa-sk -C "your_email@example.com"
    ```
    ````

4. When you are prompted, touch the button on your hardware security key.

5. When you are prompted to "Enter a file in which to save the key," press `Enter` to accept the default file location.
    ```
    > Enter a file in which to save the key (/Users/YOU/.ssh/id_ed25519_sk):[Press enter]
    ```

6. When you are prompted to type a passphrase, press `Enter`.
    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```

7. Add the SSH public key to your account on GitHub.
`````

`````{tab-item} macOS
If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key.

1. Insert your hardware security key into your computer.

2. Open Terminal.

3. Paste the text below, replacing the email address in the example with the email address associated with your account on GitHub.
    ```
    ssh-keygen -t ed25519-sk -C "your_email@example.com"
    ```
    ````{note}
    If the command fails and you receive the error `invalid format` or `feature not supported`, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
    ```
    ssh-keygen -t ecdsa-sk -C "your_email@example.com"
    ```
    ````

4. When you are prompted, touch the button on your hardware security key.

5. When you are prompted to "Enter a file in which to save the key," press `Enter` to accept the default file location.
    ```
    > Enter a file in which to save the key (/Users/YOU/.ssh/id_ed25519_sk):[Press enter]
    ```

6. When you are prompted to type a passphrase, press `Enter`.
    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```

7. Add the SSH public key to your account on GitHub.
`````

`````{tab-item} Windows
If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key.

1. Insert your hardware security key into your computer.

2. Open Git Bash.

3. Paste the text below, replacing the email address in the example with the email address associated with your account on GitHub.
    ```
    ssh-keygen -t ed25519-sk -C "your_email@example.com"
    ```
    ````{note}
    If the command fails and you receive the error `invalid format` or `feature not supported`, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
    ```
    ssh-keygen -t ecdsa-sk -C "your_email@example.com"
    ```
    ````

4. When you are prompted, touch the button on your hardware security key.

5. When you are prompted to "Enter a file in which to save the key," press `Enter` to accept the default file location.
    ```
    > Enter a file in which to save the key (c:\Users\YOU\.ssh\id_ed25519_sk):[Press enter]
    ```

6. When you are prompted to type a passphrase, press `Enter`.
    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```

7. Add the SSH public key to your account on GitHub.
`````
``````

### Adding a new SSH key to your GitHub account

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account#adding-a-new-ssh-key-to-your-account):

``````{tab-set}
````{tab-item} Ubuntu
You can add an SSH key and use it for authentication, or commit signing, or both. If you want to use the same SSH key for both authentication and signing, you need to upload it twice.

After adding a new SSH authentication key to your account on GitHub.com, you can reconfigure any local repositories to use SSH.

1. Copy the SSH public key to your clipboard. 

    If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.
    ```
    $ cat ~/.ssh/id_ed25519.pub
    # Then select and copy the contents of the id_ed25519.pub file
    # displayed in the terminal to your clipboard
    ```
    ```{tip}
    Alternatively, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.
    ```

2. In the upper-right corner of any page on GitHub, click your profile photo, then click `Settings`.
   
3. In the "Access" section of the sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-hidden="true"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> `SSH and GPG keys`.
   
4. Click `New SSH key` or `Add SSH key`.
   
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop".
   
6. Select the type of key, either authentication or signing.
    
7. In the "Key" field, paste your public key.
    
8. Click `Add SSH key`.
    
9. If prompted, confirm access to your account on GitHub.
````

````{tab-item} macOS
You can add an SSH key and use it for authentication, or commit signing, or both. If you want to use the same SSH key for both authentication and signing, you need to upload it twice.

After adding a new SSH authentication key to your account on GitHub.com, you can reconfigure any local repositories to use SSH.

1. Copy the SSH public key to your clipboard. 

    If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.
    ```
    $ pbcopy < ~/.ssh/id_ed25519.pub
    # Copies the contents of the id_ed25519.pub file to your clipboard
    ```
    ```{tip}
    If `pbcopy` isn't working, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.
    ```

2. In the upper-right corner of any page on GitHub, click your profile photo, then click `Settings`.
   
3. In the "Access" section of the sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-hidden="true"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> `SSH and GPG keys`.
   
4. Click `New SSH key` or `Add SSH key`.
   
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop".
   
6. Select the type of key, either authentication or signing.
    
7. In the "Key" field, paste your public key.
    
8. Click `Add SSH key`.
    
9. If prompted, confirm access to your account on GitHub.
````

`````{tab-item} Windows
You can add an SSH key and use it for authentication, or commit signing, or both. If you want to use the same SSH key for both authentication and signing, you need to upload it twice.

After adding a new SSH authentication key to your account on GitHub.com, you can reconfigure any local repositories to use SSH.

1. Copy the SSH public key to your clipboard. 

    If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.
    ```
    $ clip < ~/.ssh/id_ed25519.pub
    # Copies the contents of the id_ed25519.pub file to your clipboard
    ```
    ````{note}
    * With Windows Subsystem for Linux (WSL), you can use `clip.exe`. Otherwise if `clip` isn't working, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.
    * On newer versions of Windows that use the Windows Terminal, or anywhere else that uses the PowerShell command line, you may receive a `ParseError` stating that `The '&lt;' operator is reserved for future use.` In this case, the following alternative `clip` command should be used:
    ```
    $ cat ~/.ssh/id_ed25519.pub | clip
    # Copies the contents of the id_ed25519.pub file to your clipboard
    ```
    ````

2. In the upper-right corner of any page on GitHub, click your profile photo, then click `Settings`.
   
3. In the "Access" section of the sidebar, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-key" aria-hidden="true"><path d="M10.5 0a5.499 5.499 0 1 1-1.288 10.848l-.932.932a.749.749 0 0 1-.53.22H7v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22H5v.75a.749.749 0 0 1-.22.53l-.5.5a.749.749 0 0 1-.53.22h-2A1.75 1.75 0 0 1 0 14.25v-2c0-.199.079-.389.22-.53l4.932-4.932A5.5 5.5 0 0 1 10.5 0Zm-4 5.5c-.001.431.069.86.205 1.269a.75.75 0 0 1-.181.768L1.5 12.56v1.69c0 .138.112.25.25.25h1.69l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l.06-.06v-1.19a.75.75 0 0 1 .75-.75h1.19l1.023-1.025a.75.75 0 0 1 .768-.18A4 4 0 1 0 6.5 5.5ZM11 6a1 1 0 1 1 0-2 1 1 0 0 1 0 2Z"></path></svg> `SSH and GPG keys`.
   
4. Click `New SSH key` or `Add SSH key`.
   
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop".
   
6. Select the type of key, either authentication or signing.
    
7. In the "Key" field, paste your public key.
    
8. Click `Add SSH key`.
    
9. If prompted, confirm access to your account on GitHub.
`````
``````

### Testing your SSH connection

From [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection):

`````{tab-set}
````{tab-item} Ubuntu
1. Open Terminal.

2. Enter the following:
    ```
    ssh -T git@github.com
    # Attempts to ssh to GitHub
    ```
    You may see a warning like this:
    ```
    > The authenticity of host 'github.com (IP ADDRESS)' can't be established.
    > ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
    > Are you sure you want to continue connecting (yes/no)?
    ```

3. Verify that the fingerprint in the message you see matches [GitHub's public key fingerprint](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints). If it does, then type `yes`:
    ```
    > Hi USERNAME! You've successfully authenticated, but GitHub does not
    > provide shell access.
    ```
    You may see this error message:
    ```
    ...
    Agent admitted failure to sign using the key.
    debug1: No more authentication methods to try.
    Permission denied (publickey).
    ```
    This is a known problem with certain Linux distributions. 
    ```{note}
    The remote command should exit with code 1.
    ```

4. Verify that the resulting message contains your username.
````

````{tab-item} macOS
1. Open Terminal.

2. Enter the following:
    ```
    ssh -T git@github.com
    # Attempts to ssh to GitHub
    ```
    You may see a warning like this:
    ```
    > The authenticity of host 'github.com (IP ADDRESS)' can't be established.
    > ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
    > Are you sure you want to continue connecting (yes/no)?
    ```

3. Verify that the fingerprint in the message you see matches [GitHub's public key fingerprint](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints). If it does, then type `yes`:
    ```
    > Hi USERNAME! You've successfully authenticated, but GitHub does not
    > provide shell access.
    ```
    ```{note}
    The remote command should exit with code 1.
    ```

4. Verify that the resulting message contains your username.
````

````{tab-item} Windows
1. Open Git Bash.

2. Enter the following:
    ```
    ssh -T git@github.com
    # Attempts to ssh to GitHub
    ```
    You may see a warning like this:
    ```
    > The authenticity of host 'github.com (IP ADDRESS)' can't be established.
    > ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
    > Are you sure you want to continue connecting (yes/no)?
    ```

3. Verify that the fingerprint in the message you see matches [GitHub's public key fingerprint](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints). If it does, then type `yes`:
    ```
    > Hi USERNAME! You've successfully authenticated, but GitHub does not
    > provide shell access.
    ```
    ```{note}
    The remote command should exit with code 1.
    ```

4. Verify that the resulting message contains your username.
````
`````

## Submitting issues

If you are experiencing issues with any code or content of a repository (such as this operating manual you are reading right now), you can submit issues. For doing so go to the dashboard of the corresponding repository and press the `Issues` tab where you can open a new request.

For example you encounter a bug or a mistake in this operating manual, please visit this [repository](https://github.com/duckietown/docs-opmanual_duckiebot/issues) to open a new issue.

## Git troubleshooting

```{todo}
Use the `trouble` directive instead
```

### Problem 1: https instead of ssh:

The symptom is:

    $ git push
    Username for 'https://github.com':

Diagnosis: the `remote` is not correct.

If you do `git remote` you get entries with `https:`:

    $ git remote -v
    origin  https://github.com/duckietown/Software.git (fetch)
    origin  https://github.com/duckietown/Software.git (push)

Expectation:

    $ git remote -v
    origin  git@github.com:duckietown/Software.git (fetch)
    origin  git@github.com:duckietown/Software.git (push)

Solution:

    git remote remove origin
    git remote add origin git@github.com:duckietown/Software.git


### Problem 2: `git push` complains about upstream

The symptom is:

    fatal: The current branch ![branch name] has no upstream branch.

Solution:

    $ git push --set-upstream origin ![branch name]
