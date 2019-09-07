# Context Processors

### Project-Level ```context_processors.py```

```context_processors``` return dicts of items as context to be rendered within templates.

```python
from django.contrib.sites.models import Site
from django.conf import settings as django_settings


# More Code

def settings(request):
    ctx = {
        "ADMIN_URL": django_settings.ADMIN_URL,
        "CONTACT_EMAIL": django_settings.CONTACT_EMAIL,
        # More code
    }

    if Site._meta.installed:
        site = Site.objects.get_current(request)
        ctx.update({
            "SITE_NAME": site.name,
            "SITE_DOMAIN": site.domain
        })
    return ctx
```


## Sites Framework and Fixtures

```python
SITE_ID = int(os.environ.get("SITE_ID", 1))
```

## Project-Level ```sites.json``` Fixtures File

Pinax starter projects include a fixtures file, which contain data that Django can load directly into the database at the start of the project, rather than later, through the website itself.

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

## Passing Sites Variables into Templates

```python
{% blocktrans with site_name=current_site.name site_url=current_site %}
```

```python
{{ site_name }}
```



### Project-Level ```context_processors.py```

```python
from django.contrib.sites.models import Site
from django.conf import settings as django_settings


def pinax_apps_filter(app):
    return app.startswith("pinax.") or app in ["account", "mailer"]


def package_names(names):
    apps = []
    for x in names:
        if x.startswith("pinax."):
            apps.append(x.replace(".", "-"))
        if x == "account":
            apps.append("django-user-accounts")
        if x == "mailer":
            apps.append("django-mailer")
    return apps
```

Findng the right app- Alternate

```python
def settings(request):
    ctx = {
        "ADMIN_URL": django_settings.ADMIN_URL,
        "CONTACT_EMAIL": django_settings.CONTACT_EMAIL,

        "pinax_notifications_installed": "pinax.notifications" in django_settings.INSTALLED_APPS,
        "pinax_stripe_installed": "pinax.stripe" in django_settings.INSTALLED_APPS,

        "pinax_apps": package_names(filter(pinax_apps_filter, django_settings.INSTALLED_APPS))
    }
    # More Code
```
