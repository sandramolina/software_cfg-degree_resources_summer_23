# Package Management

At some point in your programming career, you'll want to ~~cheat~~ use other people's code in your own project. Both Python and node have very large repositories of code at your disposal that you can use for all manner of things. By far the most extensive repositories (for all intents and purposes, you can regard these as a monopoly) are [PyPI](https://pypi.org/) and [npm](https://www.npmjs.com/)

This guide is supposed to be an introduction to 'vanilla' package management using `pip` for Python and `npm` for node. There are fancier package management tools out there (like [`conda`](https://docs.conda.io/en/latest/) for (mainly) Python, and [`yarn`](https://yarnpkg.com/) for node), but both plain-old `pip` and `npm` are widely used (and you are required to understand these before you use anything else).

The concepts outlined below are general enough to apply to almost any modern programming language, with a specific focus on how things work for Python and node.

## How do they work?

Anything other than the most basic of projects will require you to bring in libraries from third-parties. In the root directory of your project, there might be a file that defines what libraries are needed to run your code, and what versions are acceptable (typically also a `lock` file that **locks in** the ***exact*** version of a module).

In Python, using `pipenv`, this file is called the `Pipfile`, and in node it is called the `package.json` file. They serve (broadly-speaking) the same purpose, just for different languages.

In Python, using `venv`, the relevant libraries are stored in the `lib` folder, and are automatically made available to your Python code.

There are two approaches to where the code for these third-party libraries are stored.
* In a central, but local repository (e.g. for `mvn` in the Java world, all the third-party code can be found in `~/.m2/repository`)
* In a local folder (for Python in a folder called *the virtual environment*, in node a folder called `node_modules`)

In this course, you should only be concerned about the second approach as that is the one used for the languages that you are using. However, at some point in your career, you'll probably have to deal with languages that follow the first approach.

## Python and Pip

There are two common ways of initializing a virtual environment for your project. PyCharm will initialize one for you, but if you want to use a more basic code editor (like vim, or VS Code), you will need to do this directly at the command line. Fortunately, this is fairly simple.

### venv

* Navigate to the root folder of your new project
* Run `python -m venv venv`
* To **activate** your virtual environment (i.e. to install stuff to your virtual environment using `pip`, and make all installed libraries available to your code), run `source ./venv/bin/activate` (POSIX) or `source ./venv/bin/Activate.ps1` (Powershell)
* Install a library using `pip install requests` (for example)
* To **deactivate** your virtual environment, just type `deactivate`
* To delete your virtual environment, just delete the `venv` folder with `rm -rf venv` from the root of your project.

### pipenv

This is probably my preferred way of initiating a virtual environment, mainly because it most resembles the way other languages do it.

You'll have to install the `pipenv` program first. You can do this using `pip install --user pipenv`.

Then

* Navigate to the root folder of your new project
* Install a library using `pipenv install requests`
* You'll notice a `Pipfile` that contains information about what libraries are installed, and a `Pipfile.lock` that specifies exactly what version of your libraries are installed, in your folder
* If you're interested, you can type `pipenv --venv` to find out where `pipenv` has put your virtual environment

## Node and npm

* Navigate to the root folder of your new project
* `npm init`
* Answer the questions
* You'll notice a new `package.json` in the root of your project
* Install a library using `npm install axios` (for example)
* You notice a new entry in `package.json` for your library, a `package-lock.json` file which specifies exactly what versions of which libraries are installed and a `node_modules` folder where your libraries are stored