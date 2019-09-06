# High Level Variables

## Django Version

The Django version that you specify when you create your project will be inserted throughout your Pinax starter project using the ```{{ django_version }}``` variable, to avoid hard coding.

## Project Name Variable

The project name that you specify when you create your project will be inserted throughout your Pinax starter project using the ```{{ project_name }}``` variable, to avoid hard coding.

## App Config

### Project-Level

Within the project-level ```__init__.py``` file, the ```default_app_config``` path is set:

```python
default_app_config = "{{ project_name }}.apps.AppConfig"
```

The ```default_app_config``` path leads to the  project-level ```apps.py```, where ```{{ project_name }}``` is assigned to the ```AppConfig``` class ```name``` variable.

```python
from django.apps import AppConfig as BaseAppConfig


class AppConfig(BaseAppConfig):

    name = "{{ project_name }}"
```

### App-Level

The following piece of code, found in the app-level root ```__init__.py``` works similarly to sys.path. It will add all of the subdirectories named after the package to the package's path.

```python
from pkgutil import extend_path
__path__ = extend_path(__path__, __name__)  # noqa
```

Within the app directory, the ```__init__.py``` sets the ```__version__``` and ```default_app_config``` path for the app.

```python
import pkg_resources


__version__ = pkg_resources.get_distribution("pinax-<app>").version
default_app_config = "pinax.<app>.apps.AppConfig"
```

The ```default_app_config``` path leads to the package ```apps.py```, where the package's ```name``` is set. The ```AppConfig.ready()``` method can also be overriden here, often to include special settings or receivers when Django starts running.

```python
from importlib import import_module

from django.apps import AppConfig as BaseAppConfig


class AppConfig(BaseAppConfig):

    name = "pinax.<app>"

    def ready(self):
        import_module("pinax.<app>.receivers")
```
