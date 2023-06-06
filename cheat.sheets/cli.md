# The Command Line

The command line (also known as **the terminal** or **the shell**) is the most direct route into the heart of your computer. As such, it is inevitable that you will need to use it.

## A potted history

When UNIX mainframes were really the only computers that the public would ever use, the main interface to the computer was through remote 'dumb' terminals: computer monitors with a keyboard attached that you would type commands into which the computer would execute. A single mainframe would commonly serve an entire group of users (e.g. all the users at a University). The main language that would be used in these terminals was called a **shell**.

On UNIX machines these days (including Linux and Macs), dumb terminals have been replaced by **terminal emulators**, and the terms **terminal**, **shell** and **command line** are pretty much used interchangeably to refer to the same thing.

When DOS came along (on which Windows is built), the DOS command line was a not-so-subtle copy of the shell that came along with powerful UNIX machines. The DOS command line is still central to how Windows works, and unfortunately has evolved separately from UNIX shells.

## The situation today

Most UNIX machines come with a version of what's called a **POSIX** shell. On macos, the [Z shell](https://en.wikipedia.org/wiki/Z_shell) (or **zsh**) is used, whereas on Linux, the [Bourne Again Shell](https://www.gnu.org/software/bash/) (or **bash**) is generally used. Other shells exist, but **POSIX** shells are (more or less) interchangeable.

Windows still uses DOS, but another emerging shell exists called (**Powershell**)[https://github.com/PowerShell/PowerShell]. **Powershell** is also available for UNIX machines, but really, no-one outside of the Windows world uses **Powershell**. Fortunately, there are pieces of software that emulate **bash** well enough for most users (noticeably (**mingw**)[https://en.wikipedia.org/wiki/MinGW] and (**cygwin**)[https://www.cygwin.com/]). Luckily, when you install (**git**)[https://git-scm.com/], a trimmed-down version of **cygwin** is installed.

Furthermore, Windows now has the ability to run Linux directly within it using a system called (**WSL**)[https://learn.microsoft.com/en-us/windows/wsl/install]. I haven't used Windows for a long time, but I hear nice things: however, it's not quite frictionless yet, and its use is probably reserved for the more advanced user.

## Starting the shell

### macos

macos has a built-in terminal emulator called **Terminal**. You can launch it as you would any other program on macos. My preferred way is to use the spotlight search (mostly because you can do it entirely using the keyboard).

* Press CMD+SPACE together to bring up the spotlight search
* Start typing 'Terminal'
* Press RETURN to launch it

### Windows

The terminals that you can launch on Windows are **cmd**, **Powershell** and **bash** (if you have a version installed). If you have enabled **WSL**, you'll also have a **bash** there too, but be warned: it has its idiosyncrasies, and you're kind of on your own. If you want **bash** on Windows, stick to **bash for git** (which you'll have to install).

All of these shells can be launched like any program.

* Press the START button to bring up the start menu
* Start typing the name of your shell (i.e. `cmd`, `powershell` or `bash`)
* Highlight the program you wish to launch
* Press RETURN to launch it

Be warned that you can also launch **Powershell** as an administrator: this will be required if you are installing programs using the shell.

## Some common commands

These commands are **POSIX** compliant, meaning that they will work on both **bash** and **zsh**. They may also work for **cmd** and **Powershell**: you'll have to try them to see.

### General

* Arrow up for previous command executed
* CTRL-C to kill a hanging command
* TAB for autocomplete
  * if this beeps, press TAB again
* Paste the clipboard
  * INSERT for Windows
  * CMD-V for Macos
  * CTRL-SHIFT-V for Linux
* Copy output of a command to the clipboard
  * `<command> | clip` for Windows
  * `<command> | pbcopy` for Macos
  * `<command> | xclip --selection c` for Linux

### Navigating the directory tree

* `pwd` - Present working directory
* `cd` - Change directory to HOME
* `cd ..` - Change to parent directory
* `cd <path>` - Change to `<path>` directory
* `ls` - Show contents of a directory
* `ls -lah` - Show contents of a directory, one line per file/directory, include hidden files

### File manipulation

* `touch <filename>` - Create an empty (text) file
* `echo '<something>' >> <filename>` - Append `<something>` to a file
* `echo '<something>' > <filename>` - Replace the contents of a file with `<something>`
* `cat <filename>` - Print out the contents of a (text) file
* `mv <filename> <new_filename>` - Move a file
* `cp <filename> <new_filename>` - Copy a file