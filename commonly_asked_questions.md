# Commonly Asked Questions

Answers to questions commonly asked about Pinax

## `DisallowedHost`

```python
DisallowedHost at /
Invalid HTTP_HOST header: '127.0.0.1:8000'. You may need to add '127.0.0.1' to ALLOWED_HOSTS.
```

## My Templates Aren't Working Properly

```python
npm install
pip install -r requirements.txt
./manage.py migrate
./manage.py loaddata sites
npm run dev
```

Browse to http://localhost:3000/

## Collect Static
