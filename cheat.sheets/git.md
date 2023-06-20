# git

## Installation

Instructions on how to install `choco` (for Windows) or `brew` (for macos) can be found [here](./install.software.md)

The below commands will also install `gitk`, a basic GUI. You can run this from the command line from any repository. `gitk --all` will give you a graph of all git branches on that repository. `gitk &` will run `gitk` 'in the background' (so that the terminal won't wait until it's finished running).

### Windows

From Powershell with Administrator rights, run

```bash
choco install git
```

### macos

```bash
brew install git
brew install git-gui
```

## Setup SSH key

You will also need to set up an SSH key. Running 

```bash
ssh-keygen
```

will set one up in the standard location: your public key will be at `~/.ssh/id_rsa.pub`. This is the key that you can safely share with Github and Gitlab. Do not share your private key (`~/.ssh/id_rsa`) with anyone.

## Setup Github

### Share SSH key with Github

* Open your public key using VS Code

```
code ~/.ssh/id_rsa.pub
```

* Copy the contents of the public key to your clipboard
* Open [Github](https://github.com/)
  * Set up an account if you have not done so already
  * Click on your avatar at the top left
  * Navigate to settings
  * Click on SSH and GPG keys on the left
  * Add new SSH key

## Config

* `git config --global core.editor "code --wait"` - Use VS Code as default editor
* `git config --global --add --bool push.autoSetupRemote true` - Set upstream automatically (note this only works in very recent versions of `git`: you may come across older versions of `git` that don't support this)
* `git config --global user.name "Mona Lisa"` - Configure the username in `git`. Note, this is *NOT* the username you use to log into Github or Gitlab, merely the name of the user recorded in git logs
* `git config user.email "youremail@yourdomain.com"` - Configure the email in `git`. Note, this is *NOT* the email you use to log into Github or Gitlab, merely the email of the user recorded in git logs
  * Please note that in public repositories, this email will be exposed to the public, making it a potential victim of spambots and hackers. If you don't want to expose your email address to the public, then either set up a 'junk' email address, or set a random email address here.

## Workflow

* `git add -A` - Add all new changes to all new files to the staging area
* `git commit -m "<some_message>"` - Create a commit from all files in the staging area
* `git push` - 'Push' your changes to the git server (usually the repository in Github)
  * Usually, the first time you push a branch, `git` will ask you to set an upstream branch. Read the instructions that `git` spits out carefully. Alternatively, use config to auto-setup the upstream branch.
* `git pull` - 'Pull' changes on the server on the upstream branch and synchronize your local branch to it.
* `git fetch` - 'Fetch' all changes on the server that are not in your local clone. This does not change your local branches, but it updates your local copies of remote branches so that `git pull` has less to do
* `git checkout -b <new_branch>` - Create a new branch, and switch to it
* `git checkout <branch>` - Checkout an existing branch