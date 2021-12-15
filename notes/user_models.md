# Custom User Models

Even though Django ships with a built-ing User model for authentication, 
the Django team *highly recommends* using a custom user model for our projects. 
This allows for far more flexibility down the line.

## Setup

We'd start by taking the usual steps in starting up a Django project and app. 
Make sure to not run the `migrate` command until after the custom user model 
has been made.

## Creating Custom User Model

First place we should start is in the `settings.py` file for our project. Here, 
we want to add our app to `INSTALLED_APPS` and set `AUTH_USER_MODEL` to what will 
end up being our custom user model.

After that, we'd to the `models.py` file in our app, and create a new User model. 
That user model would look somewhat like this:

```python
from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    pass
    # add additional fields in here

    def __str__(self):
        return self.username
```

Now we need to make two new forms that we'll commonly use to work with users. 
Since we need forms, we need to make a `forms.py` file within our app and populate it
with this:

```python
from django import forms
from django.contrib.auth.forms import UserCreationForm, UserChangeForm
from .models import CustomUser

class CustomUserCreationForm(UserCreationForm):

    class Meta:
        model = CustomUser
        fields = ('username', 'email')

class CustomUserChangeForm(UserChangeForm):

    class Meta:
        model = CustomUser
        fields = ('username', 'email')
```

Lastly, we have to update `admin.py` in our app:

```python
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin

from .forms import CustomUserCreationForm, CustomUserChangeForm
from .models import CustomUser

class CustomUserAdmin(UserAdmin):
    add_form = CustomUserCreationForm
    form = CustomUserChangeForm
    model = CustomUser
    list_display = ['email', 'username',]

admin.site.register(CustomUser, CustomUserAdmin)
```

Now we can run `makemigrations` and `migrate` to create a database that uses 
our custom user model.
