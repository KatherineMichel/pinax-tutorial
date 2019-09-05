# Overview of How a Vanilla Django Project Works

## Creating a Vanilla Django Project from Scratch

To create a vanilla Django project from scratch, the developer installs Django, probably within a virtual environment. Django itself is a Python package published to PyPI and will be installed within the project's site packages directory. The developer can now enter a command into the command line to create a vanilla Django project that will include the default Django templates. The project will be installed within the directory of choice, often the home directory, with the Django app(s) installed within the Django project.

It's very likely that the code developed through this project will be used for this project only.

## Typical Vanilla Django Project and App Structure 

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
