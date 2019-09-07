# Setting Up Your Development Environment

## Schools of Thought

There are two schools of thought about developer tools. Some developers have opinionated views about which tools are the best. Other developers believe that it's not the tools that matter, but what you do with them. Ultimately, the tools you choose should be the ones that enable you to work at your best.

## Python, pip, pip3, and virtualenv

To complete this tutorial, you will need to have Python and pip or pip3 installed. Also, use of a virtual environment is recommended for Python projects.

### Python

Your computer might have come with Python already installed. If not, you can install Python from the official [Python downloads page](https://www.python.org/downloads). It's recommended that you use Python 3.x. Support for Python 2 will end soon.

You can verify that Python 2 or Python 3 is installed by checking the version.

```shell
$ python --version
```

```shell
$ python3 --version
```

### pip and pip3

[pip](https://pip.pypa.io) is a popular Python package manager used to easily install packages. If you have installed Python from the official Python downloads page, you should also have pip or pip3 installed. pip has been used with Python 2 and pip3 was created for Python 3.

You can verify that pip or pip3 is installed by checking the version.

```shell
$ pip --version
```

```shell
$ pip3 --version
```

The following is the syntax for installing a package with pip or pip3.

```shell
$ pip install <package>
```

```shell
$ pip3 install <package>
```

### Global Install, Local Install, and virtualenv

Python and pip or pip3 should now be installed globally on your computer, meaning that they are accessible from anywhere on your computer.

However, it's recommended that you create and activate a virtual environment, and install your Django project and its packages within the virtual environment. The project and its packages will be isolated within the virtual environment, in order to avoid conflicts with other projects.

If you install a Python version or Python package globally, then later install a different version globally (overriding the first version), any project not installed within a virtual environment might break if it depends on the first version. Installing a project and its packages in a virtual environment prevents this.

You can create a virtual environment by using the virtualenv command or through the use of a virtualenv manager such as Pipenv. 

## Package Management

Although individual packages can be installed using pip or pip3, many Django projects, such as Pinax starter projects, have a list of packages to be installed in order for the project to work. The installation of this list of packages can be automated in more than one way.

### requirements.txt

For many years, packages were commonly installed using [pip](https://pip.pypa.io) and a [requirements.txt file](https://pip.pypa.io/en/stable/user_guide/#requirements-files) containing a list of the packages.

### Pipenv

In 2017, [Pipenv](https://docs.pipenv.org) was authored as a virtualenv manager that replaces requirements.txt by automating the use of pip, virtualenv, Pipfile, and Pipfile.lock. Pipenv automatically creates virtualenvs for your projects, adds or removes packages from your Pipfile, and generates the Pipfile.lock for deterministic builds.

Pipenv can be installed using pip or pip3. 

```shell
$ pip install pipenv
```

```shell
$ pip3 install pipenv
```

## npm

Pinax uses npm, a JavaScript package manager, to manage front-end dependencies. If Node.js is installed on your computer, npm will be installed as well. If not, you can install npm from the official [Get npm! page](https://www.npmjs.com/get-npm).

You can verify that npm is installed by checking the version 

```shell
$ npm -v
```

## Alternative Methods of Software Installation

So far, we have used the official software download pages for installing software. There are other methods of installing software. For instance, many Mac users find the Mac package manager [Homebrew](https://brew.sh) to be a convenient way to install software.

## IDEs and Text Editors

IDE stands for Integrated Development Environment. An IDE can make writing code easier for you. Visual Studio Code, PyCharm, and Sublime Text are popular choices for Python development, but there are many great IDEs and text editors to choose from. You can learn more on the official [Python Integrated Development Environments (IDEs) page](https://wiki.python.org/moin/IntegratedDevelopmentEnvironments).
