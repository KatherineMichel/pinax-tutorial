# Django User Account Signals and Receivers

In Pinax starter projects that include Django User Accounts (Pinax Accounts, Documents, Social Auth, and Team Wiki), signals and receivers are used to communicate from the app to the project that an event has occurred. This is the Observer design pattern. In these Pinax starter projects, you will find a standard file named ```receivers.py```. In the Django User Accounts package, you will find a file named signals.py. 

A signal is sent to the receiver when the following events have occurred:

```python
user_sign_up_attempt
```

```python
user_signed_up
```

```python
user_login_attempt
```

```python
user_logged_in
```

```python
password_changed
```

## Project-Level ```receivers.py```

The project ```receivers.py``` contains the receivers:

```python
from django.dispatch import receiver

from account.signals import password_changed
from account.signals import user_sign_up_attempt, user_signed_up
from account.signals import user_login_attempt, user_logged_in

from pinax.eventlog.models import log


@receiver(user_logged_in)
def handle_user_logged_in(sender, **kwargs):
    log(
        user=kwargs.get("user"),
        action="USER_LOGGED_IN",
        extra={}
    )


@receiver(password_changed)
def handle_password_changed(sender, **kwargs):
    log(
        user=kwargs.get("user"),
        action="PASSWORD_CHANGED",
        extra={}
    )


@receiver(user_login_attempt)
def handle_user_login_attempt(sender, **kwargs):
    log(
        user=None,
        action="LOGIN_ATTEMPTED",
        extra={
            "username": kwargs.get("username"),
            "result": kwargs.get("result")
        }
    )


@receiver(user_sign_up_attempt)
def handle_user_sign_up_attempt(sender, **kwargs):
    log(
        user=None,
        action="SIGNUP_ATTEMPTED",
        extra={
            "username": kwargs.get("username"),
            "email": kwargs.get("email"),
            "result": kwargs.get("result")
        }
    )


@receiver(user_signed_up)
def handle_user_signed_up(sender, **kwargs):
    log(
        user=kwargs.get("user"),
        action="USER_SIGNED_UP",
        extra={}
    )
```
