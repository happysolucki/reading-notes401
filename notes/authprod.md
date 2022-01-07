# Authentication and Production Server

## JSON Web Tokens

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and
self-contained way for securely transmitting information between parties as a
JSON object. This information can be verified and trusted because it is digitally signed.

JWTs are generally used for authorization. When a user is logged into a site,
each subsequent request includes a JWT, which is then used to give the user
access to routes, services, and resources that are permitted with that token.

## DRF JWT Authentication

In order to incorporate JWTs with a Django app that uses DRF, we need to install
the `djangorestframework_simplejwt` library:

```python
# pip
pip install djangorestframework_simplejwt

# poetry
poetry add djangorestframework_simplejwt
```

We then need to update our `settings.py` and `urls.py` files:

##### settings.py

```python
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```

##### urls.py

```python
from django.urls import path
from rest_framework_simplejwt import views as jwt_views

urlpatterns = [
    # Your URLs...
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
]
```

### Usage

#### Obtain Token

To authenticate and obtain a token, we need to hit the `/api/token` endpoint. 
It only accepts **POST** requests. For example, we'd send a username & password 
in our post request.

The response we should get should include an access and refresh token. Once we 
get those, they should be stored on the client side, usually in localStorage.

If we have protected views on the backend, the **access token** should be in the 
header of all requests.

#### Refresh Token

Access tokens expire after five minutes, so we need refresh tokens to get new 
access tokens. To do this, we need to hit the `/api/token/refresh` endpoint along with 
posting the refresh token.

This request return a new **access token** that should be used for subsequent 
requests.

The **refresh token** is only valid for 24 hours, so when it expires the user 
will need to go through the full authentication process again with their username 
and password.

## Django Production Server

The Django vehemently discourages using `python manage.py runserver` in a production 
environment. If we want to push a Django project to production, we need a web 
server like Nginx and an application server like Gunicorn. The `uwsgi.py` file 
in our Django projects contains a function to be called by the application server. 
This function gets a Python object representing the incoming request.

This function calls your code, and produces a response object which is passed to 
the WSGI server. There the response is translated into a HTTP response and is passed 
back to the web server, which finally delivers it to the user.
