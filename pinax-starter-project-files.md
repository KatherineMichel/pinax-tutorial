# Pinax Starter Project Files

Within Pinax starter projects and apps, you will find all of the files commonly found in Django projects and apps, plus some specific to Pinax.

## Configuration Files

Pinax starter projects include the following standard Django project configuration files:

| Folder/File                | Description                                                           |
| -------------------------- | --------------------------------------------------------------------- |
| manage.py                  | Convenience script used to run administrative tasks                   |
| Pipfile                    | Pipenv file used to install and unintall packages deterministically   |
| project_name/_init_.py     | Python file that indicates a directory should treated as a package    |
| project_name/apps.py       | Application configuration file                                        |
| project_name/settings.py   | Project-level settings file                                           |
| project_name/wsgi.py       | A Web Server Gateway Interface file                                   |

## General Django Files

Pinax starter projects include the following general Django project files:

| Folder/File                | Description                                                           |
| -------------------------- | --------------------------------------------------------------------- |
| project_name/urls.py       | Project-level URLs file                                               |
| project_name/views.py      | Project-level views file                                              |

## Pinax Starter Project Specific Files

Pinax starter projects typically include additional Pinax starter project files, such as:

| Folder/File                        | Description                                                           |
| ---------------------------------  | --------------------------------------------------------------------- |
| fixtures/sites.json                |                                                                       |
| project_name/context_processors.py | Project-level context-processors file                                 |
| project_name/hooks.py              | Project-level hooks file                                              |
| project_name/receivers.py          | Project-level receivers file                                          |

## Test Files

| Folder/File                         | Description                                                      |
| ----------------------------------- | ---------------------------------------------------------------- |
| static/src/tests/example.html       |                                                                  |

