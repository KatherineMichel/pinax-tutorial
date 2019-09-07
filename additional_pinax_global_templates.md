# Additional Pinax Global Templates

<!--
See also DUA and Pinax Stripe
-->

Templates that begin with an underscore are partial templates included in other templates.

## '_nav.html'

<!--
uncomment
-->

The ```_nav.html``` template fragment included in the global ```base.html``` template provides the navbar markup. 

```html
<ul class="main-bar">
    <li><a href="#">One</a></li>
    <li><a href="#">Two</a></li>
</ul>
```

## '_messages.html'

The ```_messages.html``` template fragment included in the global ```base.html``` template provides the Django messages framework markup. 

```html
{% for message in messages %}
    <div class="message {{ message.tags }}">
        <button type="button" class="close" data-dismiss="message"><i  class="fas fa-times"></i></button>
        {{ message }}
    </div>
{% endfor %}
```

<!--
/* global $ */

const handleMessageDismiss = () => {
  $('.message button[data-dismiss="message"]').click((e) => {
    $(e.currentTarget).closest('.message').remove();
  });
};

export default handleMessageDismiss;
-->

## '_pagination.html'

```html
{# Pagination for default django.core.paginator.Paginator #}
{# This template will work with CBV views with ``paginate_by`` specified. #}
{% load i18n %}

{% if is_paginated %}
<nav class="page-navigation" aria-label="page navigation">
    <ul>
        {% if page_obj.has_previous %}
            <li class="prev">
                <a href="?page={{ page_obj.previous_page_number|stringformat:"d" }}{{ getvars }}{{ hashtag }}">
                    <i class="fas fa-long-arrow-alt-left"></i>
                    {% trans "Previous" %}
                </a>
            </li>
        {% else %}
            <li class="prev disabled">
                <a>{% block pagination_previous_label %}<i class="fas fa-long-arrow-alt-left"></i> {% trans "Previous" %}{% endblock %}</a>
            </li>
        {% endif %}
        {% for page in paginator.page_range %}
            <li class="{% ifequal page page_obj.number %}active{% endifequal %}">
                <a href="?page={{ page|stringformat:"d" }}{{ getvars }}{{ hashtag }}">{{ page|stringformat:"d" }}</a>
            </li>
        {% endfor %}
        {% if page_obj.has_next %}
            <li class="next">
                <a href="?page={{ page_obj.next_page_number|stringformat:"d" }}{{ getvars }}{{ hashtag }}">
                    {% trans "Next" %}
                    <i class="fas fa-long-arrow-alt-right"></i>
                </a>
            </li>
        {% else %}
            <li class="next disabled">
                <a>{% block pagination_next_label %}
                    {% trans "Next" %}
                    <i class="fas fa-long-arrow-alt-right"></i>
                    {% endblock %}
                </a>
            </li>
        {% endif %}
    </ul>
</nav>
{% endif %}
```

## 'subnav_base.html'

```html
{% extends "site_base.html" %}

{% load i18n %}

{% block body %}
    <div class="subnav-container">
        {% block subnav %}
        {% endblock %}
        <section>
            {% block content %}
            {% endblock %}
        </section>
    </div>
{% endblock %}
```

## HTTP Error Message Templates

### `404.html`

```html
{% extends "site_base.html" %}

{% load i18n %}

{% block head_title %}{% trans "Not Found" %}{% endblock %}

{% block body %}
    <header class="server-error page-not-found">
        <h1>{% trans "Page not found" %}</h1>
        <p>{% trans "We're sorry but that page could not be found." %}</p>
    </header>
{% endblock %}
```

### `500.html`

```html
{% extends "site_base.html" %}

{% load i18n %}

{% block head_title %}{% trans "Server Error" %}{% endblock %}

{% block body %}
    <header class="server-error internal-server-error">
        <h1>{% trans "Something went wrong" %}</h1>
        <p>{% trans "We're sorry but a server error has occurred. We've been notified and will look into it as soon as possible." %}</p>
    </header>
{% endblock %}
```
