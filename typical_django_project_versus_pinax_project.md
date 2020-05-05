# Typical Django Project Versus Pinax Project

## Creating a Typical Django Project from Scratch

When a typical Django project is created from scratch, Django is installed first, perhaps within a virtual environment. The Django source code package itself is a Python package published to PyPI that will be downloaded from PyPI and installed in the project's site-packages directory. The author can now manually enter the ```startproject``` command into the command line to create a Django project that will include the default Django templates. The project will now be installed within the author's directory of choice, often the home directory, with the Django app(s) installed within the Django project.

## Typical Django Project and App Structure 

```shell
directory_name/
|-- project_name/
|    |-- app_name/                <-- Django app
|    |    |-- __init__.py
|    |    |-- admin.py
|    |    |-- apps.py
|    |    |-- migrations/
|    |    |    |-- __init__.py
|    |    |-- models.py
|    |    |-- tests.py
|    |    |-- views.py
|    |-- project_name/            <-- Django project
|    |    |-- __init__.py
|    |    |-- settings.py
|    |    |-- urls.py
|    |    |-- wsgi.py
|    |-- manage.py
|-- venv/ (if used)
``` 

## How Pinax Projects and Apps Are Different

The Pinax ecosystem includes a handy command line interface tool called [Pinax CLI](https://github.com/pinax/pinax-cli) that can be used to install a Pinax starter project locally in place of a regular Django project.

The Pinax CLI uses the ```django.core.management.call_command()``` to automatically call the ```startproject``` command from within the Pinax CLI script, using the Pinax starter project package stored on GitHub as the Django ```template``` instead of the default Django template.

Once the Pinax starter project has been installed, the project dependencies, including the Pinax apps that have already been included in the project, can be installed.

Depending on which Pinax starter project version you are using, each Pinax starter project contains a requirements.txt file or Pipfile listing the required dependency versions, in order to create a deterministic project build.

In a vanilla Django project, the apps are installed within the project itself. Because Pinax apps are packages, they will instead be downloaded from the Python Package Index [PyPi](https://pypi.org) and installed in the project's site-packages directory, along with the other project packages. Because Pinax apps provide the website functionality, you might not need to install a new Django app.

Once the packages are installed and listed in the ```INSTALLED_APPS``` section of the project's ```settings.py``` file, Python will use [sys.path](https://docs.python.org/3/library/sys.html#sys.path) in the ```sys``` module to locate the packages in the site-packages directory and use them as if installed directly in the project.

## Example Pinax Starter Project and Packages Directory Structure

Below is an example computer home directory layout where your Pinax starter project directory and your .local directory (containing your project's packages directory) might co-exist.

Within .local directory, your virtualenv directory will contain a project directory. In the project directory you will find the Python installation which will include a site-packages directory that will contain the Django source code package and any Pinax app packages you have installed.

```shell
.local/
|-- bin/
|-- lib/
|-- share/
|    |-- virtualenvs/                
|    |    |-- pinax-project/
|    |    |    |-- bin/
|    |    |    |-- include/
|    |    |    |-- lib/
|    |    |    |    |-- python3.6/
|    |    |    |    |    |-- site-packages/
|    |    |    |    |    |    |-- django/                  <-- Django source code
|    |    |    |    |    |    |-- pinax/
|    |    |    |    |    |    |    |-- app-name/           <-- Pinax app
|    |    |    |    |    |    |    |    |-- __init__.py 
|    |    |    |    |    |    |    |    |-- admin.py 
|    |    |    |    |    |    |    |    |-- apps.py 
|    |    |    |    |    |    |    |    |-- migrations/ 
|    |    |    |    |    |    |    |    |    |-- __init__.py 
|    |    |    |    |    |    |    |    |-- models.py 
|    |    |    |    |    |    |    |    |-- tests.py
|    |    |    |    |    |    |    |    |-- views.py 

directory_name/
|-- project_name/
|    |-- project_name/            <-- Pinax starter project
|    |    |-- __init__.py
|    |    |-- settings.py
|    |    |-- urls.py
|    |    |-- wsgi.py
|    |-- manage.py
|-- venv/ (if used)
```

## How to Locate Your Packages

Locating and looking through your project packages installed on your computer can help you to better understand how your project, and Python in general, work. You can also make changes within your package locally to test or customize your project.

### Hidden Files

Packages are stored in a hidden directory that you need to unhide in order to find the packages. Hidden folders and files start with a dot and are called dot folders and files.

On a Mac, one easy way to unhide and hide hidden folders and files is to toggle back and forth using the key combination ```command + shift + .```.
