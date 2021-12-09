# Django Models

In Django applications, we access and manage data through models. Models define 
the *structure* of stored data, including the field types and possibly also
their maximum size, default values, selection list options, help text for
documentation, label text for forms, etc. The definition of the model is 
independent of the database we choose to use.

Generally, models are defined in a app's **models.py** file. They are
implemented as subclasses of django.db.models.Model, and can include fields,
methods and metadata. Here's an example of how we'd go about making a model:

```python
from django.db import models

class Snack(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    name = models.CharField(max_length=64)
    description = models.TextField()

    def __str__(self):
        return self.name
```
