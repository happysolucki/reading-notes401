# Django REST Framework & Docker

## Docker

Docker is kinda just Linux containers. It's somewhat similar to a virtual machine. 
With Docker we can faithfully reproduce a production environment locally. It also 
allows us to share our Docker instances with others for easier collaboration. 

### Images and containers

Images and containers are the two fundamental concepts to grasp when you start
with Docker. An image is a snapshot in time of what a project *contains*.
A container is a running instance of the image.

Bringing about images and containers is somewhat like baking a cake:

- A `Dockerfile` is the recipe for a cake
- An *image* is a snapshot of the recipe at a given time
- A docker-compose.yml says how to make the cake
- And the *container* is the actual, baked cake

In reference to the recent lab we did in forming a posts api, the *image* is 
the environment in which we made the django project and built out the api with tools 
like Django REST Framework. It's all wrapped up in a minified python distro. 
The *container* is a live instance of our project, which is likely running on port 
8000 if the directions were followed.

## Django REST Framework

Using Django REST Framework with our Django projects allows us to more easily 
build web APIs. It simplifies the process of serializing ORM and non-ORM data sources. 
Serialization allow complex data such as querysets and model instances to be
converted to native Python datatypes that can then be easily rendered into JSON,
XML or other content types. It also gives us access to use cleaner views whenever 
we hit our API endpoints in the browser.
