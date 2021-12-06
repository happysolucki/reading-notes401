# Django Forms

In regards to forms, Django handles three parts:

- preparing and restructuring data to make it ready for rendering

- creating HTML forms for the data

- receiving and processing submitted forms and data from the client

## The Django Form class

A _Form_ class desribes a form and determines how it works and appears. A 
form class's fields map to HTML form `<input>` elements.

A form’s fields are themselves classes; they manage form data and perform 
validation when a form is submitted. A _DateField_ and a _FileField_ handle 
very different kinds of data and have to do different things with it.

When we instantiate a form, we can opt to leave it empty or pre-populate it, 
for example with:

- data from a svaed model instance (as in the case of admin forms for editing)

- data that we have collated from other sources

- data received from a previous HTML form submission

## Building a form in Django

### The Form class

If we already have in mind what our HTML form should look like, we'll start 
off like this:

```python
from django import forms

class NameForm(forms.Form):
    your_name = forms.CharField(label='Your name', max_length=100)
```

This form will render like this in HTML initially:

```html
<label for="your_name">Your name: </label>
<input id="your_name" type="text" name="your_name" maxlength="100" required>
```

Since this doesn't include `<form>` tags or a submit button, we'll have to 
provide those in our template.

## The view

To handle the form we need to instantiate it in the view for the URL where we 
want it to be published:

```python
from django.http import HttpResponseRedirect
from django.shortcuts import render

from .forms import NameForm

def get_name(request):
    # if this is a POST request we need to process the form data
    if request.method == 'POST':
        # create a form instance and populate it with data from the request:
        form = NameForm(request.POST)
        # check whether it's valid:
        if form.is_valid():
            # process the data in form.cleaned_data as required
            # ...
            # redirect to a new URL:
            return HttpResponseRedirect('/thanks/')

    # if a GET (or any other method) we'll create a blank form
    else:
        form = NameForm()

    return render(request, 'name.html', {'form': form})
```

## The template

Now we don't have much left to do in the template:

```html
<form action="/your-name/" method="post">
    {% csrf_token %}
    {{ form }}
    <input type="submit" value="Submit">
</form>
```
