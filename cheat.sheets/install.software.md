# Installing software through the command line

## Why?

The normal way of installing software on Macs and Windows boxes is to navigate to the relevant website, download the package, and either run the installer, or copy the application into your applications folder.

Anyone who is used to a system with a decent package manager (e.g. Linux) will find this rather... quaint. For instance, on my current Linux box, to install mysql-workbench, I just open a [terminal](./cli.md) and type `sudo apt install mysql-workbench`. Within about half a minute, the thing is installed and configured.

More worryingly, it's incredibly easy to fall foul of a spoof site where you will inadvertently download and install a version of the software you want that is riddled with [trojans](https://en.wikipedia.org/wiki/Trojan_horse_(computing)), [adware](https://en.wikipedia.org/wiki/Adware) and other non-desirable plugins that can be extremely hard to clean.

Even worse, installer programs are of varying quality. Oracle's installers, for instance, are notoriously complex: the mySQL installer for Windows is one of the worst pieces of software that I've ever seen.

Yet worse, the uninstallers can often be extremely messy, and incomplete. I've seen all sorts of detritis left behind by uninstall scripts, and over time, these can clog up and slow down your computer.

## Package managers to the rescue

Luckily, some bright sparks have written package managers for Windows and Mac, the most famous of which are [choco](https://chocolatey.org/) for Windows, and [brew](https://brew.sh/) for Mac. Install these: you can thank me later.

### Chocolatey (Windows)

* Open **Powershell** ***as an administrator***: this won't work if you open **Powershell** as a normal user
* Go to the [installation](https://chocolatey.org/install) page
* Scroll down to the really long installation script and copy it. They've even provided you with a copy button
* Paste that command in your **Powershell**
* Done

### Homebrew (Mac)

* Open **Terminal**
* Got to the [home](https://brew.sh/) page
* Copy the really long installation script. They've even provided you with a copy button
* Paste that commadn in your **Terminal**
* Done

## Things you can install

Personally, when I have to use Windows or Macs, the first thing that I install is either **choco** or **brew**. Everything else I install using them. This results in an installation that is exactly like most other developers, and is preconfigured with sensible defaults.

You can try some of the following as examples. If you're feeling really keen, uninstall the ones that you've installed already and reinstall them using **choco** or **brew**.

Windows users, you have to run the `choco` command using **Powershell** ***AS AN ADMINISTRATOR***. Mac users can just use a plain old *terminal*.

| Program | choco | brew |
|-|-|-|
| Google Chrome | `choco install googlechrome` | `brew install --cask google-chrome` |
| git | `choco install git` | `brew install git` |
| VS Code | `choco install vscode` | `brew install --cask visual-studio-code` |
| mySQL Workbench | `choco install mysql.workbench` | `brew install --cask mysqlworkbench` |
| PyCharm | `choco install pycharm-community` | `brew install --cask pycharm` |

## Installing programming languages

So, this is a little more complicated. If you are happy with just using the latest version of Python or Node, then go ahead and `choco install python` or `brew install python` (or `nodejs`/`node` for node). For now, this will suffice for learning purposes, but sooner or later, you will run into versioning issues.

However, most professional developers will need to switch between different versions of their favourite tools. For instance, you may have to work on one part of your system that uses Python 3.6, and won't work with later versions, but newer parts of your system use Python 3.10.

Luckily, this is a common enough problem that some nice folks have written version managers for the most common languages.

### asdf (Macs and Linux only)

Sorry, Windows folks, this won't work for you.

[`asdf`](https://asdf-vm.com/) is a version manager for pretty much any programming language that you could possibly ever want. In particular, it works really well for Python and node.

* Make sure that you have `git` installed: see above for the `brew` command
* Go to the [home](https://asdf-vm.com/guide/getting-started.html) page
* Install the dependencies you need on the system that you're on (so, use the `brew` command for macs, for instance)
* Download `asdf` using the `git` command supplied.
  * You can also use the `brew` command supplied, but I had troubles with this: if you go down this route, you're on your own
* Scroll down to the relevant shell/installation route (probably `ZSH and git`)
* Follow the instructions. At the time of writing, it was:
  * Open `~/.zshrc` in your favourite text editor (probably VS Code)
  * Add `. "$HOME/.asdf/asdf.sh"` to the end of that file
  * Restart your shell

To install Python with asdf, do the following. Note, this will also install `pip` for you.

* `asdf plugin-add python`
* `asdf install python 3.11.3` - this is the latest version at the time of writing
* `asdf global python 3.11.3` - this will set Python to use version 3.11.3 everywhere
* Restart your terminal

Typing `which python` in your terminal will show you where `python` is located: you'll need this to set the correct `python` interpreter in Pycharm at some point.

Typing `python --version` will confirm what version of `python` you are using.

To install node with asdf, do the following. Note, this will also install `npm` for you.

* `asdf plugin-add nodejs`
* `asdf install nodejs 18.16.0` - this is the latest [LTS](https://nodejs.org/en/download) at the time of writing
* `asdf global nodejs 18.16.0` - this will set node to use version 18.16.0 everywhere
* Restart your terminal

### Version management for Windows

The solution to the versioning problem is a bit more complicated. `asdf` is a very new solution, and at the time of writing, no-one has ported it to Windows.

The older single-language versions are available, however. Unfortunately, I don't have a Windows box to play with, so I can't verify any of the below. Perhaps some kind soul will update these instructions later.

#### Python

Try using [pyenv](https://pyenv-win.github.io/pyenv-win/). You **should** be able to install it using `choco install pyenv-win`

#### Node

Try using [nvm](https://github.com/coreybutler/nvm-windows). You **should** be able to install it using `choco install nvm`