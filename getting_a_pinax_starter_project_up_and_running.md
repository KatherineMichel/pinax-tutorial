# Getting A Pinax Starter Project Up and Running

First, we will install the Pinax starter project and its packages in your local development environment.

## Make and Change Directory

You will need to make a directory, then change directory into it.

```shell
$ mkdir <directory-name>
$ cd <directory-name>
```

## pip Versus pip3

In this part of the tutorial, we will be assuming you are using pip3, but you could also use pip.

## Create a Virtual Environment

Use of a virtual environment is recommended for Python projects.

### Create a Virtual Environment Using Pipenv and Python 3

The Pinax starter projects have been updated to install virtualenvs and packages by using Pipenv by default. 

```shell
$ pipenv --three
$ pipenv shell
```

### Create a Virtual Environment Using virtualenv

Alternatively, you can create and activate the virtualenv directly.

```shell
$ pip3 install virtualenv
$ virtualenv <my-site-env>
$ source <my-site-env>/bin/activate
```

## Install Pinax CLI

Pinax CLI can be installed using pip. 

```shell
$ pip3 install pinax-cli
```

## Pinax Starter Projects List

Once Pinax CLI is installed, you can view the list of available Pinax starter project releases by using the ```pinax projects``` command. Projects with an official release will have a version number next to their name. Projects without an official release will not.

```shell
$ pinax projects
```

## Install Pinax Starter Project

You can specify via the command line which Pinax starter project you want to install, and what name to give your project. Pinax CLI identifies and downloads the correct tagged release of that Pinax starter project.

```shell
$ pinax start <starter-project-name> <project-name>
```

Example

```shell
$ pinax start account mysite
```

This is the equivalent of:

```shell
$ pip3 install Django==2.0
$ django-admin startproject --template=https://github.com/pinax/pinax-starter-projects/zipball/account mysite
```

## ```--dev``` Flag

Pinax starter project development versions can also be installed using the ```--dev``` flag. Pinax starter projects without an official release will need to be installed this way. 

```shell
$ pinax projects
$ pinax start --dev <starter-project-name> <project-name>
```

### Location Flag

Optionally, you can use the location flag to specify project location. By using this, the project files will be installed within the current directory, rather than within a directory inside of your current directory.

```shell
$ pinax start <starter-project-name> <project-name> --location .
```

## Run Your Project on a Local Server

Next, we will get your project up and running on a local server. Doing so enables you to view a private version of your website in your browser as you make changes.

### npm Static Build Process

Pinax uses npm, a JavaScript package manager, to manage front-end dependencies. It's important to follow the additional npm steps. Otherwise, your project design will not render properly! 

First, install npm in your project

```shell
$ npm install
```

### Install Your Packages Using Pipenv

If you are using an up-to-date Pinax starter project, install your packages using Pipenv and Pipfile

```shell
$ pipenv install
```

### Install Your Packages Using requirements.txt

If you are using an older version of a Pinax starter project, you can still install the packages using requirements.txt. If needed, change directory into the project directory that contains the requirements.txt file, then install your packages.

```shell
$ cd mysite
$ pip3 install -r requirements.txt
```

### Migrate and Load Fixtures

The ```migrate``` command applies your model information to your database.

```shell
$ ./manage.py migrate
```

The ```loaddata``` command loads fixtures data into the database. 

```shell
$ ./manage.py loaddata sites
```

Add ```"127.0.0.1"``` to ```ALLOWED_HOSTS```

```python
ALLOWED_HOSTS = [
    "localhost",
    "127.0.0.1",
]
```

### Open a Second Terminal Window

In order to run both npm for frontend, and Django for backend, we will need to open two terminal windows. 

### npm Run Server

In the first terminal window, use the npm ```start``` command to run the frontend server

```shell
$ npm start
```

### Traditional Run Server

In the second terminal window, use the Django ```runserver``` command to run the backend server.

```shell
$ ./manage.py runserver
```

Browse to http://localhost:8000/
