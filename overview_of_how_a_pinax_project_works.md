# Overview of How a Pinax Project Works

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
