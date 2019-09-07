# Django User Accounts

## What is Django User Accounts?

Django User Accounts is a Pinax package used for account management. Django User Accounts extends (not replaces) Django's default user model. Django User Accounts extends the default user model because reusable apps won't work together if a custom user model is used in one of the apps.

Several Pinax starter projects include the Django User Accounts package. Django user Accounts can also be integrated into non-Pinax projects.

## What is Included in Django User Accounts?

* Anonymous user account creation
* User account creation
* Confirmation email and signup code
* Signup, login, logout, and other views
* Account deletion
* Password reset and management

## `settings.AUTH_USER_MODEL`

In keeping with Django best practice for packages and user authentication, throughout Pinax starter projects and apps, the user is indicated through the model fields ```ForeignKey``` and ```settings.AUTH_USER_MODEL```. 

Example

```python
user = models.ForeignKey(settings.AUTH_USER_MODEL, related_name="related_name", on_delete=models.CASCADE)
```

Although the user is referred to as ```user``` in this example, depending on the functionality of the app, the user might be referred to as something else, such as ```author```. However, regardless of what the user database field is named, the ```settings.AUTH_USER_MODEL``` in each app's user model links these variables together to form one user instance via ```django.contrib.auth``` in the settings.py file.
