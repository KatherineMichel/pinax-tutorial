# Django User Account Templates

<!--
## '_account_bar.html'

_account_bar.html template is different than other one

The optional ```_account_bar.html``` template fragment is included in the global ```base.html``` for apps that include Django User Accounts.

```html
{% load i18n %}
{% load account_tags %}


<ul class="account-bar">
    {% if request.user.is_authenticated %}
        <li class="user">
            <i class="fas fa-user"></i>
            {% user_display request.user %}
        </li>
        <li class="settings">
            <a href="{% url 'account_settings' %}">
                <i class="fas fa-cog"></i>
                {% trans "Settings" %}
            </a>
        </li>
        <li class="logout">
            <a id="account_logout" href="{% url 'account_logout' %}">
                <i class="fas fa-power-off"></i>
                {% trans "Log out" %}
            </a>
        </li>
    {% else %}
        <li><a href="{% url 'account_login' %}">{% trans "Log in" %}</a></li>
        {% if ACCOUNT_OPEN_SIGNUP %}
            <li><a href="{% url 'account_signup' %}">{% trans "Sign up" %}</a></li>
        {% endif %}
    {% endif %}
</ul>

<form id="accountLogOutForm" style="display: none;" action="{% url 'account_logout' %}" method="POST">
    {% csrf_token %}
</form>
```
-->

## 'base.html'

<!--
includes Pinax Stripe
-->

```html
{% extends "subnav_base.html" %}

{% load i18n %}

{% block body_class %}account{% endblock %}

{% block subnav %}
<nav class="settings-nav">
    <div class="heading">Settings</div>
    <a class="account-settings" href="{% url "account_settings" %}">
        {% trans "Account" %}
    </a>
    <a class="account-password" href="{% url "account_password" %}">
        {% trans "Change password" %}
    </a>
    <a class="account-delete" href="{% url "account_delete" %}">
        {% trans "Delete account" %}
    </a>

    {% if pinax_notifications_installed %}
        <a class="notice-settings" href="{% url "pinax_notifications:notice_settings" %}">
            {% trans "Notices" %}
        </a>
    {% endif %}

    {% if pinax_stripe_installed %}
        <div class="heading">Billing</div>
        <a class="pinax-stripe-subscriptions" href="{% url "pinax_stripe_subscription_list" %}">
            {% trans "Subscriptions" %}
        </a>
        <a class="pinax-stripe-payment-methods" href="{% url "pinax_stripe_payment_method_list" %}">
            {% trans "Payment Methods" %}
        </a>
        <a class="pinax-stripe-invoices" href="{% url "pinax_stripe_invoice_list" %}">
            {% trans "Invoices" %}
        </a>
    {% endif %}
</nav>
{% endblock %}
```

## 'settings.html'

```html
{% extends "account/base.html" %}

{% load i18n %}
{% load bootstrap %}

{% block body_class %}account account-settings{% endblock %}

{% block head_title %}{% trans "Account" %}{% endblock %}

{% block content %}
    <form method="POST" action="{% url "account_settings" %}">
        <legend>{% trans "Account" %}</legend>
        {% csrf_token %}
        {{ form|bootstrap }}
        <div class="form-actions">
            <button>{% trans "Save" %}</button>
        </div>
    </form>
{% endblock %}
```

## 'signup.html'

```html
{% extends "site_base.html" %}

{% load account_tags %}
{% load i18n %}
{% load bootstrap %}

{% block body_class %}account account-signup{% endblock %}
{% block head_title %}{% trans "Sign up" %}{% endblock %}

{% block body %}
    <form id="signup_form" method="post" action="{% url "account_signup" %}" autocapitalize="off" {% if form.is_multipart %} enctype="multipart/form-data"{% endif %}>
        <legend>{% trans "Sign up" %}</legend>
        {% csrf_token %}
        {{ form|bootstrap }}
        {% if redirect_field_value %}
            <input type="hidden" name="{{ redirect_field_name }}" value="{{ redirect_field_value }}" />
        {% endif %}
        <div class="form-actions">
            <button>{% trans "Sign up" %}</button>
        </div>
        <p class="login-signup">
            {% trans "Already have an account?" %}
            <a href="{% urlnext 'account_login' %}">{% trans "Log in" %}</a>
        </p>
    </form>
{% endblock %}

{% block scripts %}
    {{ block.super }}
    <script type="text/javascript">
        $(document).ready(function() {
            $('#id_username').focus();
        });
    </script>
{% endblock %}
```

