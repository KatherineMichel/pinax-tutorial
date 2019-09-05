# Overview of How a Pinax Project Works

Pinax starter projects, apps, and themes work differently than vanilla Django projects and apps. 

Pinax starter projects, apps, and themes began as vanilla Django projects and were developed to provide specific functionality. Afterward, instead of being used only for one project, they were packaged to reuse and share.

The Pinax starter project provides the Django project framework and the self-contained Pinax apps that come pre-installed as packages provide the functionality needed for the project.

The Pinax ecosystem includes a handy command line interface tool called [Pinax CLI](https://github.com/pinax/pinax-cli) that can be used to install a Pinax starter project locally, just like a default Django project, in the directory of your choice, often the home directory. 

A default Django project can be created via the command line using the ```startproject``` command. The Pinax CLI uses the ```django.core.management.call_command()``` to automatically call the ```startproject``` command from within the Pinax CLI script, using the URL to the chosen Pinax starter project package stored on GitHub as the Django ```template``` instead of the default Django template.

Once the Pinax starter project has been installed, the project dependencies, including the Pinax apps that have already been included in the project, can be installed.

Depending on which Pinax starter project version you are using, each Pinax starter project contains a requirements.txt file or Pipfile listing the required dependency versions, in order to create a deterministic project build.

In a vanilla Django project, the apps are installed within the project itself. Because Pinax apps are packages, they will not be installed within the project itself. They will instead be downloaded from the Python Package Index [PyPi](https://pypi.org) and installed in the project's site-packages directory, along with the other project packages. 

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
