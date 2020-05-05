# How a Typical Django Project Works Versus How a Pinax Project Works

## Creating a Django Project from Scratch

To create a Django project from scratch, first install Django, perhaps within a virtual environment. The Django source code package itself is a Python package published to PyPI that will be downloaded from PyPI and installed in the project's site-packages directory. You can now enter a command into the command line to create a Django project that will include the default Django templates. The project will be installed within your directory of choice, often the home directory, with the Django app(s) installed within the Django project.

It's very likely that the code developed through this project will be used for this project only.

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
