# Global Settings

<!--
WEBPACK_LOADER = {
    "DEFAULT": {
        "CACHE": not DEBUG,
        "BUNDLE_DIR_NAME": "/",
        "STATS_FILE": os.path.join(PROJECT_ROOT, "webpack-stats.json"),
        "POLL_INTERVAL": 0.1,
        "TIMEOUT": None,
        "IGNORE": [".*\.hot-update.js", ".+\.map"]
    }
}
-->

A settings.py file contains the high-level settings for a Django project. Pinax uses some default Django settings, as well as some settings specific to Pinax. The following are settings that all Pinax starter projects have in common.

## Development Environment

### ```os``` Module

The Python ```os``` module provides a platform-independent interface between Django and the computer's operating system.

```python
import os
```

### ```DATABASES```

The ```DATABASES``` setting provides a default [SQLite](https://www.sqlite.org/index.html) database configuration. Because SQLite is included with Python, no additional configuration is needed to use it. However, SQLite is not recommended for use in production. The ```NAME``` setting corresponds to the name of the database file on your computer.

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.sqlite3",
        "NAME": "dev.db",
    }
}
```

### ```ALLOWED_HOSTS```

The ```ALLOWED_HOSTS``` setting provides the host/domain name(s) that are allowed to be served. This is a security measure to prevent HTTP Host header attacks. 

```python
ALLOWED_HOSTS = [
    "localhost",
]
```

### ```SECRET_KEY```

```SECRET_KEY``` is a cryptographic signing variable used for Django instance installation. ```SECRET_KEY``` should be set to a unique, unpredictable value and kept secret.

```python
SECRET_KEY = "{{ secret_key }}"
```

### ```DEBUG```

With ```DEBUG``` as ```TRUE```, Django will provide a detailed traceback when exceptions occur. ```DEBUG``` should be set to ```FALSE``` in production, as a security measure.

```python
DEBUG = True
```

### Web Server Gateway Interface (WSGI)

The Web Server Gateway Interface (WSGI) enables communication between the web server and Django.

```python
WSGI_APPLICATION = "{{ project_name }}.wsgi.application"
```

## Installed Apps

Django maintains a registry of all apps installed in a project.

Apps listed in ```INSTALLED_APPS``` are ordered by built-in Django apps, templates, then external apps, including Pinax apps. Pinax includes all of the standard Django built-in apps, plus sites.

If you are using a Pinax starter project, the names of the Pinax apps included in the project will likely already be listed in the ```INSTALLED_APPS``` section of the settings.py file. However, it's not uncommon in Django development to need to add an app name, for instance, if you add an additional app to the project yourself. 

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.messages",
    "django.contrib.sessions",
    "django.contrib.sites",
    "django.contrib.staticfiles",

    # templates
    "bootstrapform",
    "pinax.templates",

    # external
    "account",
    "pinax.<app>",

    # project
    "{{ project_name }}",
]
```

<!--
why is project_name listed? Because installed through Pinax CLI?

regular Django apps
-->

## Middleware

<!--
sessions, authentication, messages
https://docs.djangoproject.com/en/2.0/topics/http/middleware/
-->

Middleware hooks into Django's request and response processing.

```python
MIDDLEWARE = [
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    "django.middleware.csrf.CsrfViewMiddleware",
    "django.contrib.auth.middleware.AuthenticationMiddleware",
    "django.contrib.messages.middleware.MessageMiddleware",
    "django.middleware.clickjacking.XFrameOptionsMiddleware",
]
```

## Path

<!--
https://stackoverflow.com/questions/21005822/what-does-os-path-abspathos-path-joinos-path-dirname-file-os-path-pardir
https://stackoverflow.com/questions/38412495/difference-between-os-path-dirnameos-path-abspath-file-and-os-path-dirnam

Package root is stored in a variable called BASE_DIR. 

PROJECT_ROOT - folder that contains setting.py
PROJECT_ROOT is BASE_DIR + your_project_name
BASE_DIR contains PROJECT_ROOT (where manage.py is)

PROJECT_ROOT/PACKAGE_ROOT
-->

```python
PROJECT_ROOT = os.path.abspath(os.path.join(os.path.dirname(__file__), os.pardir))
PACKAGE_ROOT = os.path.abspath(os.path.dirname(__file__))
BASE_DIR = PACKAGE_ROOT
```

<!--
```shell
directory_name/
|-- PROJECT_ROOT/
|    |-- PACKAGE_ROOT/            <-- Pinax starter project
|    |    |-- __init__.py
|    |    |-- settings.py
|    |    |-- site_media.py
|    |    |    |-- static/
|    |    |-- urls.py
|    |    |-- wsgi.py
|    |-- manage.py
|-- venv/ (if used)
```
-->

### Static Files

Static files are the CSS, JavaScript, and image files that have been added to the site by a web developer, not user.

The ```STATIC_ROOT``` is the absolute path to the directory where static files will be collected for deployment after the ```collectstatic``` command has been run. The ```STATIC_ROOT``` path is ```PACKAGE_ROOT/site_media/static```.

<!--
Files should not be placed here, happens automatically
-->

```python
STATIC_ROOT = os.path.join(PACKAGE_ROOT, "site_media", "static")
```

The URL to use when referring to static files located in STATIC_ROOT.

```python
STATIC_URL = "/site_media/static/"
```

Alternatively, the staticfiles could be found by traversing the path ```PROJECT_ROOT/static/dist```.

```python
STATICFILES_DIRS = [
    os.path.join(PROJECT_ROOT, "static", "dist"),
]
```

The file storage engine to use when collecting static files with the ```collectstatic``` management command.

```python
STATICFILES_STORAGE = "django.contrib.staticfiles.storage.ManifestStaticFilesStorage"
```

The finder backends that know how to find static files in various locations.

```python
STATICFILES_FINDERS = [
    "django.contrib.staticfiles.finders.FileSystemFinder",
    "django.contrib.staticfiles.finders.AppDirectoriesFinder",
]
```

### Media Files

Media files are files uploaded by the user.

The ```MEDIA_ROOT``` path is ```PACKAGE_ROOT/site_media/media```.

```python
MEDIA_ROOT = os.path.join(PACKAGE_ROOT, "site_media", "media")
```

The URL that handles the media served from MEDIA_ROOT. 

```python
MEDIA_URL = "/site_media/media/"
```

### Templates

The ```TEMPLATES``` path is ```PACKAGE_ROOT/templates```.

#### ```context_processors```

```context_processors``` return dicts of items as context to be rendered within templates.

```python
TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [
            os.path.join(PACKAGE_ROOT, "templates"),
        ],
        "APP_DIRS": True,
        "OPTIONS": {
            "debug": DEBUG,
            "context_processors": [
                "django.contrib.auth.context_processors.auth",
                "django.template.context_processors.debug",
                "django.template.context_processors.i18n",
                "django.template.context_processors.media",
                "django.template.context_processors.static",
                "django.template.context_processors.tz",
                "django.template.context_processors.request",
                "django.contrib.messages.context_processors.messages",
                "{{ project_name }}.context_processors.settings"
            ],
        },
    },
]
```

<!--
More explanation for ```context_processors```
See Project Specific Settings for additional user auth
-->

### ```ROOT_URLCONF```

The ```ROOT_URLCONF``` provides a mapping between your project URLs and view functions.

```python
ROOT_URLCONF = "{{ project_name }}.urls"
```

## Site and Fixtures

A fixtures file contains data that Django can load directly into the database at the start of the project, rather than later, for example, when a user inputs information into a website form. The ```FIXTURE_DIRS``` path is ```PROJECT_ROOT/fixtures```. The fixtures file sites.json is specified in the command line when the fixtures are loaded.

```python
FIXTURE_DIRS = [
    os.path.join(PROJECT_ROOT, "fixtures"),
]
```

```python
SITE_ID = int(os.environ.get("SITE_ID", 1))
```

<!--
fixtures/sites.json

```python
[
    {
        "pk": 1,
        "model": "sites.site",
        "fields": {
            "domain": "localhost:8000",
            "name": "example.com [localhost]"
        }
    },
    {
        "pk": 2,
        "model": "sites.site",
        "fields": {
            "domain": "example.com",
            "name": "example.com"
        }
    }
]
```
-->

## Localization

Pinax uses the default Django localization settings.

Pinax will base timezones on Coordinated Universal Time (UTC).

```python
TIME_ZONE = "UTC"
```

Pinax will use English as the standard language.

```python
LANGUAGE_CODE = "en-us"
```

Pinax will optimize for internationalization.

```python
USE_I18N = True
```

Pinax will format dates, numbers, and calendars according to the current locale.

```python
USE_L10N = True
```

Pinax will use timezone-aware datetimes.

```python
USE_TZ = True
```

## Admin and Email

```python
ADMIN_URL = "admin:index"
```

```python
CONTACT_EMAIL = "support@example.com"
```

Pinax comes with an email backend that can be used to write emails to ```stdout``` (standard output) during development, instead of sending real emails. This should not be used in production.

```python
EMAIL_BACKEND = "django.core.mail.backends.console.EmailBackend"
```

## Logging

Pinax includes a sample logging configuration. 

```python
LOGGING = {
    "version": 1,
    "disable_existing_loggers": False,
    "filters": {
        "require_debug_false": {
            "()": "django.utils.log.RequireDebugFalse"
        }
    },
    "handlers": {
        "mail_admins": {
            "level": "ERROR",
            "filters": ["require_debug_false"],
            "class": "django.utils.log.AdminEmailHandler"
        }
    },
    "loggers": {
        "django.request": {
            "handlers": ["mail_admins"],
            "level": "ERROR",
            "propagate": True,
        },
    }
}
```
