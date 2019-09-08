# Project Specific Settings

Although most settings are the same across all Pinax starter projects, a few vary sightly based on project requirements. The following settings are unique to specific projects.

## Django User Accounts and Social Auth App Django

Django User Accounts includes account configurations and Social Auth App Django includes both account and social auth configurations.

Django User Accounts and Social Auth App Django context processors

```python
TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [
            os.path.join(PACKAGE_ROOT, "templates"),
        ],
        "APP_DIRS": True,
        "OPTIONS": {
            "debug": DEBUG,
            "context_processors": [
                ...
                "account.context_processors.account",
                "social_django.context_processors.backends",
                "social_django.context_processors.login_redirect",
                ...
            ],
        },
    },
]
```

Django User Accounts variables, including email authentication in addition to username

```python
ACCOUNT_OPEN_SIGNUP = True
ACCOUNT_EMAIL_UNIQUE = True
ACCOUNT_EMAIL_CONFIRMATION_REQUIRED = False
ACCOUNT_LOGIN_REDIRECT_URL = LOGIN_REDIRECT_URL = "home"
ACCOUNT_LOGOUT_REDIRECT_URL = "home"
ACCOUNT_EMAIL_CONFIRMATION_EXPIRE_DAYS = 2
ACCOUNT_USE_AUTH_AUTHENTICATE = True
```

Django User Accounts and Social Auth App Django authentication backends

```python
AUTHENTICATION_BACKENDS = [
    "social_core.backends.twitter.TwitterOAuth",
    "account.auth_backends.UsernameAuthenticationBackend",
]
```

Social Auth App Django Twitter API keys

```python
SOCIAL_AUTH_TWITTER_KEY = ""
SOCIAL_AUTH_TWITTER_SECRET = ""
```

## Pinax Stripe

Stripe API keys

```python
PINAX_STRIPE_SECRET_KEY = ""  # begins with sk_
PINAX_STRIPE_PUBLIC_KEY = ""  # beings with pk_
```

## Pinax Blog

```python
# Turn off the admin js; probably should remove from the form
PINAX_BLOG_ADMIN_JS = []
```

## Pinax Wiki

```python
PINAX_WIKI_HOOKSET = "{{ project_name }}.hooks.ProjectWikiHookset"
PINAX_WIKI_BINDERS = [
    "{{ project_name }}.binders.UserBinder",
    "{{ project_name }}.binders.TeamBinder"
]
```

## Pinax Webanalytics

```python
Grab your own GA id and replace UA-XXXXXXXX or use another
pinax-webanalytics provider, or roll your own template.
PINAX_WEBANALYTICS_SETTINGS = {
    "google": {
        2: "UA-XXXXXXXX",
    }
}
```
