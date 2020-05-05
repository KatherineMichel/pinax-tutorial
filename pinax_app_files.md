# Pinax App Files

Within Pinax apps, you will find all of the files commonly found in Django apps, plus some specific to Pinax.

## Configuration Files

Pinax apps include the following standard Django app configuration files:

| Folder/File                         | Description                                                           |
| ----------------------------------- | --------------------------------------------------------------------- |
| _init_.py                           | Python file that indicates a directory should treated as a package    | 
| app_name/_init_.py                  | Python file that indicates a directory should treated as a package    | 
| app_name/apps.py                    | Application configuration file                                        | 
| app_name/migrations/0001_initial.py | App-level migrations file                                             | 

## General Django App Files

Pinax apps include the following general Django app files:

| Folder/File                         | Description                                                           |
| ----------------------------------- | --------------------------------------------------------------------- |
| app_name/admin.py                   | App-level admin file                                                  | 
| app_name/forms.py                   | App-level forms file                                                  | 
| app_name/models.py                  | App-level models file                                                 | 
| app_name/urls.py                    | App-level URLs file                                                   | 
| app_name/views.py                   | App-level views file                                                  |

## Pinax App Specific Files

Pinax apps typically include additional Pinax app files, such as:

| Folder/File                    | Description                                                           |
| ------------------------------ | --------------------------------------------------------------------- |
| app_name/conf.py               | App-level conf file                                                   | 
| app_name/context_processors.py | App-level context processors file                                     |
| app_name/hooks.py              | App-level hooks file                                                  |
| app_name/managers.py           | App-level managers file                                               |
| app_name/middleware.py         | App-level middleware file                                             |
| app_name/mixins.py             | App-level mixins file                                                 |
| app_name/receivers.py          | App-level receivers file                                              |
| app_name/signals.py            | App-level signals file                                                |
| app_name/templatetags/tags.py  | App-level template tags file                                          |

## Test Files

| Folder/File                         | Description                                                           |
| ----------------------------------- | --------------------------------------------------------------------- |
| app_name/tests/tests.py             | App-level tests file                                                  | 
