# [Beginner’s Guide to Docker](https://wsvincent.com/beginners-guide-to-docker/)
- Docker is a way to implement Linux containers also known as “containerization,”. For most applications, a virtual machine provides far more resources than are needed and a container is more than sufficient.

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

# [Django for APIs - Library Website](https://djangoforapis.com/library-website-and-api/)




# Additional Resources
- [Learn Django](https://learndjango.com/) 