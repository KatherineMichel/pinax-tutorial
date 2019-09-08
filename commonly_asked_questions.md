# Commonly Asked Questions

Answers to questions commonly asked about Pinax

## Basic Customizations

### Change the Website Name

<!--
{% block site_brand %}<a href="{% url "home" %}">{{ SITE_NAME }}</a>{% endblock %}
-->

A ```SITE_NAME```, if it exists, will be inserted into the ```base.html``` template via ```SITE_NAME``` variable.

```python
{% if SITE_NAME %}{{ SITE_NAME }}
```

### Change the Language Code

A language code will be inserted into the ```base.html``` template via the ```LANGUAGE_CODE``` variable in the ```settings.py``` file.

```python
{{ LANGUAGE_CODE }}
```

### Change the Page Title

<!--
base.html

What about other pages?
two of {% endblock %}
-->

```html
        <title>{% block head_title_base %}{% if SITE_NAME %}{{ SITE_NAME }} | {% endif %}{% block head_title %}{% endblock %}{% endblock %}</title>
```

### Navbar

The ```_nav.html``` template fragment included in the global ```base.html``` template provides the navbar markup. 

```html
<ul class="main-bar">
    <li><a href="#">One</a></li>
    <li><a href="#">Two</a></li>
</ul>
```

### Remove or Edit the Footer

#### Company Name

<!--
include footer

https://docs.djangoproject.com/en/2.1/ref/templates/builtins/#now
-->

```html
&lt;your company here&gt;
```

```html
{% load i18n %}

{% now "Y" as current_year %}

{% blocktrans %}
<div class="copyright">&copy; {{ current_year }} &lt;your company here&gt;</div>
{% endblocktrans %}

<div class="made-with-pinax">
    Made with Pinax
    <div class="patches">
        {% for app in pinax_apps %}
            <img src="http://pinax.github.com/pinax-design/patches/{{ app }}.svg" />
        {% endfor %}
    </div>
</div>
```

### Add Scripts

### Change the Styling

### Add Translations

### Overriding Global Settings with Project Settings

Pinax apps often include custom settings that can be used to override global settings.

Set custom setting in settings.py

```python
CUSTOM_SETTING = <setting>
```

Import settings

```python
from django.conf import settings
```

Reference custom setting

```python
settings.CUSTOM_SETTING
```

## Troubleshooting

### `DisallowedHost`

```python
DisallowedHost at /
Invalid HTTP_HOST header: '127.0.0.1:8000'. You may need to add '127.0.0.1' to ALLOWED_HOSTS.
```

### My Templates Aren't Working Properly

```python
npm install
pip install -r requirements.txt
./manage.py migrate
./manage.py loaddata sites
npm run dev
```

Browse to http://localhost:3000/

### Collect Static
