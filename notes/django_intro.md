# Intro to Django

## Object-relational mapper

In regards to data models, it can be done all with Python. We get a rich, 
dynamic database-access API by default - but we can still write SQL if 
necessary.

```python
class Band(models.Model):
    """A model of a rock band."""
    name = models.CharField(max_length=200)
    can_rock = models.BooleanField(default=True)
```

## URLs and views

Django possesses a simple and elegant way to design URL routes.

```python
from django.urls import path

from . import views

urlpatterns = [
    path('bands/', views.band_listing, name='band-list'),
    path('bands/<int:band_id>/', views.band_detail, name='band-detail'),
    path('bands/search/', views.band_search, name='band-search'),
]
```

```python
from django.shortcuts import render

def band_listing(request):
    """A view of all bands."""
    bands = models.Band.objects.all()
    return render(request, 'bands/band_listing.html', {'bands': bands})
```

## Templates

Django’s template language is designed to strike a balance between power and 
ease. It’s designed to feel comfortable and easy-to-learn to those used to 
working with HTML, like designers and front-end developers. But it is also 
flexible and highly extensible, allowing developers to augment the template 
language as needed.

```html
<html>
  <head>
    <title>Band Listing</title>
  </head>
  <body>
    <h1>All Bands</h1>
    <ul>
    {% for band in bands %}
      <li>
        <h2><a href="{{ band.get_absolute_url }}">{{ band.name }}</a></h2>
        {% if band.can_rock %}<p>This band can rock!</p>{% endif %}
      </li>
    {% endfor %}
    </ul>
  </body>
</html>
```

## Forms

Django provides a powerful form library that handles rendering forms as HTML, 
validating user-submitted data, and converting that data to native Python 
types. Django also provides a way to generate forms from your existing models 
and use those forms to create and update data.

```python
from django import forms

class BandContactForm(forms.Form):
    subject = forms.CharField(max_length=100)
    message = forms.CharField()
    sender = forms.EmailField()
    cc_myself = forms.BooleanField(required=False)
```
