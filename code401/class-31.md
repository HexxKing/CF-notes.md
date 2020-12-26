# [Beginner’s Guide to Docker](https://wsvincent.com/beginners-guide-to-docker/)
- Docker is a way to implement Linux containers also known as “containerization,”. For most applications, a virtual machine provides far more resources than are needed and a container is more than sufficient.
- Docker is a way to run Linux containers
- Containers are a lightweight alternative to Virtual Machines
- `Dockerfile` is a list of instructions for creating an image
- Images are made up of one or more layers
- Containers are a running instance of an image
- `docker-compose.yml` controls how to run the container
- Containers are stateless and ephemeral in nature. We can link the local filesystem via `volumes` but things become more complex with databases.

> Containers vs Virtual Environments
- Virtual environments are used to isolate Python software packages locally. 
- But, virtual environments can only isolate Python packages. They still rely on a global, system-level installation of Python albeit they can refer to the proper version.
- Also we can’t run a production database or other services within virtual environments so compared to Docker containers they are far more limited.

> Helpful Commands
- why do we need `ls -la` here instead of `ls`? The answer is because the container is stopped! Only running containers will appear with docker container `ls`.
- A good command to inspect Docker is `docker info` which we can run now. It will contain a lot of output but focus on the top lines which show we now have 1 container which is stopped and 1 image.
- Want to inspect just the current image? `docker image ls`

> Images and containers
- An image is a snapshot in time of what a project contains. 
  - we will create custom images and we do so using a Dockerfile. 
- A container is a running instance of the image.
  - We also will use docker-compose.yml files to run the containers.

>Images
- define the image with a Dockerfile
  - it is a list of all the requirements needed to build our image.
  - `touch Dockerfile` and cd into it
- The first instruction must be the FROM command which lets us import a base image to use for our image. This base image could be another Docker image or one we create entirely from scratch.
- `docker image build .`
  - There will be a lot of output here ending with Successfully built and the hash id for the image.
- `$ docker image ls`
  - will inspect the current image
- `docker container ls -la`
  - inspects containers, either running, paused, or stopped
  - why do we need ls -la here instead of ls? The answer is because the container is stopped! Only running containers will appear with docker container ls.

> Images and Containers
- An image is a snapshot in time of what a project contains. A container is a running instance of the image.
- we will create custom images and we do so using a Dockerfile. We also will use docker-compose.yml files to run the containers.
- we need to define the image with a Dockerfile. This is similar to a requirements.txt file; it is a list of all the requirements needed to build our image. It is simpler to have them all in one place rather than install each manually line-by-line.
```
# Dockerfile
FROM python:3
```
- The first instruction must be the FROM command which lets us import a base image to use for our image. This base image could be another Docker image or one we create entirely from scratch.

> Image Builds
- With our instructions complete it’s time to “build” or create the image for the first time. Don’t forget that period . at the end of the command!
  - `docker image build .`
  - There will be a lot of output here ending with Successfully built and the hash id for the image. 
- `docker image ls`
  - list all existing Docker images to confirm this new one has been built


> Image Layers
- Every image is made up of one or more image layers. 
- First, each image layer is immutable–unchanged–like a git commit. This helps ensure consistency when two developers build the same image. 
- The second reason is performance. Docker caches the steps in a Dockerfile to speed up subsequent builds. When a change is made to a step, all steps following it will be executed from scratch.
- For this reason, order matters in a Dockerfile. Typically you want to put code that won’t change often at the top and code that will change at the end.


> Containers
- a docker-compose.yml file is a list of container instructions.
- “Dockerize” a basic Django web app
- Docker can work to run a web application completely on its own
- `pipenv install django`
- `poetry shell`
- `django-admin startproject example_project .`
- `python manage.py runserver`
- Now let’s run all of this with Docker instead. Stop the local server with the command Control+c. And exit the virtual environment by also typing exit. 


> Dockerized Django
- `$ touch Dockerfile`
- `$ touch docker-compose.yml`
```
# Dockerfile

#Python Version
FROM python:3

#Set Environment Variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

#Set work directory
RUN mkdir /code
WORKDIR /code

# Install Dependencies
COPY requirements.txt /code/
RUN pip install -r requirements.txt

#Copy Project
COPY . /code/
```
-  `PYTHONDONTWRITEBYTECODE` will remove .pyc files from our container which is a good optimization.
- ` PYTHONUNBUFFERED` will buffer our output so it will look “normal” within Docker for us.
- The `WORKDIR` command to create and set `/code` as our default directory within Docker. That means if in the future we want to run a command like `python manage.py runserver` we don’t have to also specify it should be run in the `/code` folder.
- The `requirements.txt` contains information on our software packages so we copy that over, too. 
- And then we install Pipenv itself via pip and then run pipenv install to install the software packages in our requirements.txt.
- the very last line here is `COPY . /code/`. That means any code changes locally will be copied over. However there are no commands after that; nothing else needs to be rebuilt.
  - An important point to make here is that the order in a `Dockerfile` matters a lot. Because of layer caching when a step changes in the `Dockerfile`, all subsequent work needs to be redone.

```
# docker-compose.yml

version: '3'

services:
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8001:8000"
```
- At the top we specify we’re using the 3rd version of Docker Compose and then set up a service, which is running within our container.
  - Multiple services can run within a Docker host–for example, we might add a db service for a running PostgreSQL database in the future–but for now we have a single web service.
- We tell it to build the current directory, execute `runserver` on startup which will start the Django server. 
- Then `volumes` will sync our local directory to the Docker container. 
- the final step we expose port `8000` which is Django’s default so the container will expose it, too.
- `$ docker-compose up --build`
  - Instead of running separate commands to build the image and run the container we can do that with one now. 


# [Django for APIs - Library Website](https://djangoforapis.com/library-website-and-api/)


# Additional Resources
- [Learn Django](https://learndjango.com/) 