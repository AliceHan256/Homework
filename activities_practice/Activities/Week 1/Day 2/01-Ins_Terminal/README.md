## Pre work installation notes from PK 

## 1. Pre work installation isntructions provided to students :
A) For Windows https://coding-bootcamp-fintech-prework.readthedocs-hosted.com/en/latest/modules/get-yo-tools-installed-on-windows/

B) For Mac https://coding-bootcamp-fintech-prework.readthedocs-hosted.com/en/latest/modules/get-yo-tools-installed-on-mac/

C) For Python
https://coding-bootcamp-fintech-prework.readthedocs-hosted.com/en/latest/modules/curling-up-with-python/

Need to install below 
Chrome
Slack
Git bash ( windows only) - easy


## 2. Homebrew  install - mac only 
go to brew.sh

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## 3. SSH
### 3.1 Check if ssh key exists
ls –al ~/.ssh

### Check the directory listing to see if you already have a public SSH key. By default, the filenames of the public keys are one of the following:

id_rsa.pub
id_ecdsa.pub
id_ed25519.pub

If you don't have an existing public and private key pair, or don't wish to use any that are available to connect to GitHub, then [generate a new SSH key.](https://docs.github.com/en/github/authenticating-to-github/checking-for-existing-ssh-keys)

If you see an existing public and private key pair listed (for example id_rsa.pub and id_rsa) that you would like to use to connect to GitHub, you can [add your SSH key to the ssh-agent.](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)


### 3.2 Generate new ssh key 
#### **For mac** , try any of the following commands using *terminal*

ssh-keygen -t rsa.  # this one worked for PK
$ ssh-keygen -t ed25519 -C "your_email@example.com"
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com" # use this if you are using a legacy system that doesn't support the Ed25519 algorithm

This creates a new ssh key, using the provided email as a label.
> Generating public/private ed25519 key pair.

When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.
> Enter a file in which to save the key (/Users/you/.ssh/id_ed25519): [Press enter]

At the prompt, type a secure passphrase. For more information, see [Working with SSH key passphrases".] (https://docs.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases)
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]

#### **For windows** try any of the following commands using *git bash*
ssh-keygen -t rsa. # this one worked for PK
$ ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-keygen –t rsa –b 4096 –C "pankaj.jan83@gmail.com" # din't work for PK, use this if you are using a legacy system that doesn't support the Ed25519 algorithm

#### Checked again by ls -al ~/.ssh.  and found id_rsa.pub  or ed25519 and id_rsa files exist 

Your identification has been saved in /Users/kumarisurbhi/.ssh/id_rsa.
Your public key has been saved in /Users/kumarisurbhi/.ssh/id_rsa.pub.

SHA256:XXX..... is key gen generated


### 3.3 Adding your SSH key to the ssh-agent

Ensure the ssh-agent is running. You can use the "Auto-launching the ssh-agent" instructions in [Working with SSH key passphrases] (https://docs.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases), or start it manually:

##### ** Mac ** 
When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.

start the ssh-agent in the background
$ eval "$(ssh-agent -s)"
> Agent pid 59566

If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

First, check to see if your ~/.ssh/config file exists in the default location.

$ open ~/.ssh/config
> The file /Users/you/.ssh/config does not exist.
If the file doesn't exist, create the file.

$ touch ~/.ssh/config
Open your ~/.ssh/config file, then modify the file, replacing ~/.ssh/id_ed25519 if you are not using the default location and name for your id_ed25519 key.

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
Note: If you chose not to add a passphrase to your key, you should omit the UseKeychain line.

Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.

$ ssh-add -K ~/.ssh/id_ed25519  # If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.

Note: The -K option is Apple's standard version of ssh-add, which stores the passphrase in your keychain for you when you add an ssh key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the -K option.

If you don't have Apple's standard version installed, you may receive an error. For more information on resolving this error, see [Error: ssh-add: illegal option -- K.](https://docs.github.com/en/github/authenticating-to-github/error-ssh-add-illegal-option----k)


##### ** Windows ** 

You can use the "Auto-launching the ssh-agent" instructions in [Working with SSH key passphrases](https://docs.github.com/en/github/authenticating-to-github/working-with-ssh-key-passphrases), or start it manually:

#### start the ssh-agent in the background
$ eval `ssh-agent -s`
> Agent pid 59566
Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.

$ ssh-add ~/.ssh/id_ed25519  # If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.


### 3.4 Adding a new SSH key to your GitHub account
#### **Mac**

By this command, in your terminal, you can copy your ssh key to your clipboard:	

Copy the SSH public key to your clipboard.

If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

$ pbcopy < ~/.ssh/id_ed25519.pub # Copies the contents of the id_ed25519.pub file to your clipboard
Tip: If pbcopy isn't working, you can locate the hidden .ssh folder, open the file in your favorite text editor, and copy it to your clipboard.
If needed, modify the command as oper your .pub file as appropriate 
pbcopy < ~/.ssh/id_rsa.pub

#### **Windows**

Copy the SSH public key to your clipboard.

If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

$ clip < ~/.ssh/id_ed25519.pub # Copies the contents of the id_ed25519.pub file to your clipboard
Tip: If clip isn't working, you can locate the hidden .ssh folder, open the file in your favorite text editor, and copy it to your clipboard.
If needed, modify the command as oper your .pub file as apprpriate 
clip < ~/.ssh/id_rsa.pub

#### settings in github

In the upper-right corner of any page, click your profile photo, then click Settings.

Settings icon in the user bar
In the user settings sidebar, click SSH and GPG keys.

Authentication keys
Click New SSH key or Add SSH key.

SSH Key button
In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

Paste your key into the "Key" field.

The key field
Click Add SSH key.

The Add key button
If prompted, confirm your GitHub password.


#### ping github from terminal 

Check in your terminal/git bash if can ping github 
ping github.com
or 
ssh –T git@github.com)

#### 3.5 if needed, troubleshooting SSH 
Use steps here [Troubleshooting SSH](https://docs.github.com/en/github/authenticating-to-github/troubleshooting-ssh)


## 4. Install vs code https://code.visualstudio.com/download

	- Install code command in path

A) **Mac**  command shift p  , need to type shell command
https://code.visualstudio.com/docs/setup/mac

B) **Windows** control shift p 
https://code.visualstudio.com/docs/setup/windows
use this url to resolve https://stackoverflow.com/questions/42606837/how-do-i-use-bash-on-windows-from-the-visual-studio-code-integrated-terminal


Below are the steps mentioned in stackoverflow url : 
Install Git from https://git-scm.com/download/win
Open Visual Studio Code and press and hold Ctrl + ` to open the terminal.

Open the command palette using Ctrl + Shift + P.
Type - Select Default Shell
Select Git Bash from the options
Click on the + icon in the terminal window
The new terminal now will be a Git Bash terminal. Give it a few seconds to load Git Bash

You can now toggle between the different terminals as well from the dropdown in terminal.


## 5. Anaconda 

A)**Mac**
https://www.anaconda.com/products/individual#windows
Graphic installer downloaded


**Mac** :Was not asked the option to not select checkboxes for path ( was instructed)
**Windows** : was asked

Below commands were instructed but shell command dint work

So had to restart the terminal 
Shell command in terminal still dint work

Conda update conda worked on mac
Conda update anaconda worked on mac

On windows above dint work so we need to set path 

https://stackoverflow.com/questions/10681101/git-bash-doesnt-see-my-path

hit the windows key → enter environment → choose from settings → edit environment variables for your account → select Path variable → Edit → New.

set PATH=%PATH%;C:\Users\61452\anaconda3;C:\Users\61452\anaconda3\Scripts\


To test it, open a new dos shell, and you should be able to use conda commands now. E.g., try conda --version.


Conda Activate conda 
conda activate dev


Virtual env creation 
conda create -n dev python=3.7 anaconda  (worked on both)
conda list

mac
conda init zsh

Windows 
Conda init bash

