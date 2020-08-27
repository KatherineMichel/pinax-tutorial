# Overview of Pinax Starter Project and App Architecture

Pinax uses many of Django's built-in patterns, as well as some patterns specific to Pinax. 

## Design Choices

### Class Based Views

Pinax apps typically used Django's convenient [Class Based Views](https://docs.djangoproject.com/en/dev/topics/class-based-views/).

### contenttypes framework

Pinax apps typically uses Django's [contenttypes framework](https://docs.djangoproject.com/en/dev/ref/contrib/contenttypes/) to manage models and their relationships.

### Django User Accounts

Pinax uses [Django User Accounts](https://github.com/pinax/django-user-accounts) to extend Django's default user model, globally. Reusable apps won't work together if a custom user model is used in one of the apps.

### Signals and Receivers

Pinax uses Django's [Signals and Receivers](https://docs.djangoproject.com/en/dev/topics/signals/) framework to communicate that events have taken place.

## Packaging Utilities

### django-appconf

Pinax uses a helper class called [django-appconf](https://django-appconf.readthedocs.io) to handle Django app packaging defaults "gracefully."



