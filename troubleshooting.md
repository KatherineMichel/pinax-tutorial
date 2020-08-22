# Troubleshooting

## Pinax CLI Does Not Create Project in Directory Root

Use the `location` flag and `.` to create project in directory root

`pinax start <project-name> <my-site> --location .`

## `DisallowedHost` Error

```python
DisallowedHost at /
Invalid HTTP_HOST header: '127.0.0.1:8000'. You may need to add '127.0.0.1' to ALLOWED_HOSTS.
```

Add `127.0.0.1` to `ALLOWED_HOSTS`

```
ALLOWED_HOSTS = [
    "localhost",
    "127.0.0.1",
]
```

## My Site Style is Not Working Properly

The style files are served using npm. Make sure that you have run `npm install`

Open two terminal windows: in one run `python manage.py runserver` and in another run `npm run dev`

```python
npm install
pip install -r requirements.txt
./manage.py migrate
./manage.py loaddata sites
npm run dev
```

Browse to http://localhost:3000/

## Collect Static
