# __Django REST Framework & Docker__

## __Docker__

docker is a way to isolate and run entire applications. With Docker it doesn’t matter if you are using a Mac, Windows, or Linux computer anymore. The entire development environment is isolated: programming language, software packages, databases, and more.

With Docker we now longer have to mess around with virtual environments. We can faithfully reproduce a production environment locally. And Docker can be shared among team members so everyone is working on the same setup. Wins all around.

__What’s the downside?__ Complexity. Docker is a complex beast under the hood. However a little knowledge can take you a long way and that’s the goal of this guide!

<br>

---

<br>

### __Containers vs Virtual Environments__

If you are a Python programmer (like me) a common question at this point is, what about virtual environments? How do they differ from containers?

Virtual environments are used to isolate Python software packages locally. We can create an isolated box for individual projects so one can use Python 2.7 and Django 1.5 while another can use Python 3.5 and Django 2.1 on the same computer. Virtual environments are great.

But…virtual environments can only isolate Python packages. They still rely on a global, system-level installation of Python albeit they can refer to the proper version. So when we use Python 2.7 in a project, we’re pointing to an installation of Python 2.7 on the computer itself, not actually within the virtual environment.

Also we can’t run a production database or other services within virtual environments so compared to Docker containers they are far more limited.

<br>

---

<br>

### __Dockerized Django__

We’ll now create a Dockerfile for our image which will completely replace our local dev environment, so this will have Python 3 and Django. Then we’ll add a docker-compose.yml for the container instructions. Make each file via the command line.

    $ touch Dockerfile
    $ touch docker-compose.yml

This Dockerfile has several commands. RUN, COPY, and ADD each create a new layer.

    # Dockerfile

    # Python version
    FROM python:3.7-alpine

    # Set environment variables
    ENV PYTHONDONTWRITEBYTECODE 1
    ENV PYTHONUNBUFFERED 1

    # Set work directory
    WORKDIR /code

    # Install dependencies
    COPY Pipfile Pipfile.lock /code/
    RUN pip install pipenv && pipenv install --system

    # Copy project
    COPY . /code/

Order matters in Dockerfiles since they are executed from top-to-bottom. First we use FROM to install python:3.7-alpine as our base image and set two environment variables with ENV. The first, PYTHONDONTWRITEBYTECODE will remove .pyc files from our container which is a good optimization. The second, PYTHONUNBUFFERED will buffer our output so it will look “normal” within Docker for us.

Then we used the WORKDIR command to create and set /code as our default directory within Docker. That means if in the future we want to run a command like python manage.py runserver we don’t have to also specify it should be run in the /code folder.

The Pipfile contains information on our software packages so we copy that over, too. (Technically we could use COPY Pipfile . and because of the WORKDIR setting it would still go in the /code folder!)

And then we install Pipenv itself via pip and then run pipenv install to install the software packages in our Pipfile. Note that we added the --system tag so that software packages are available throughout the entire container, not within a virtual environment which is Pipenv’s default but doesn’t make sense here since the entire Docker container is a virtual environment.

Ok, there’s our image.

An important point to make here is that the order in a Dockerfile matters a lot. Because of layer caching when a step changes in the Dockerfile, all subsequent work needs to be redone.

For example, the very last line here is COPY . /code. That means any code changes locally will be copied over. However there are no commands after that; nothing else needs to be rebuilt. If we had put this command earlier in the Dockerfile, say, before we install the Pipfile, then every time there is a local code change all our requirements would have to be reinstalled on the image. Wasteful.

Without going too far down this rabbit hole, remember that order is extremely important for performance and managing image size.

Now time for docker-compose.yml.

    # docker-compose.yml
    version: '3.7'

    services:
    web:
        build: .
        command: python /code/manage.py runserver 0.0.0.0:8000
        volumes:
        - .:/code
        ports:
        - 8000:8000

At the top we specify we’re using the 3.7 version of Docker Compose and then set up a service, which is running within our container.

Multiple services can run within a Docker host–for example, we might add a db service for a running PostgreSQL database in the future–but for now we have a single web service.

We tell it to build the current directory, execute runserver on startup which will start the Django server. Then volumes will sync our local directory to the Docker container. And as a final step we expose port 8000 which is Django’s default so the container will expose it, too.

Instead of running separate commands to build the image and run the container we can do that with one now. Check this out!

    $ docker-compose up --build
    Creating network "djangoapp_default" with the default driver
    Building webStep 1/6 : FROM python:3.7-alpine
    ...
    Successfully built 047a6d848c5b
    Successfully tagged djangoapp_web:latest
    Recreating djangoapp_web_1 ... done
    Attaching to djangoapp_web_1
    web_1  | Performing system checks...
    web_1  |
    web_1  | Watching for file changes with StatReloader
    web_1  | System check identified no issues (0 silenced).
    web_1  |
    web_1  | You have 17 unapplied migration(s). Your project may not work properly until you apply the migrati
    ons for app(s): admin, auth, contenttypes, sessions.
    web_1  | Run 'python manage.py migrate' to apply them.
    web_1  | January 21, 2020 - 14:49:16
    web_1  | Django version 3.0, using settings 'example_project.settings'
    web_1  | Starting development server at http://0.0.0.0:8000/
    web_1  | Quit the server with CONTROL-C.

There will be a lot of output here but if it all worked you can now visit http://127.0.0.1:8000/ in your web browser and see that Django is running entirely within a container now. Yay!

<br>

---

<br>

<br>

## __Library Website__

Django REST Framework works alongside the Django web framework to create web APIs. We cannot build a web API with only Django Rest Framework. It always must be added to a project after Django itself has been installed and configured.

In this chapter, we will review the similarities and differences between traditional Django and Django REST Framework. The most important takeaway is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

To illustrate these concepts, we will build out a basic Library website with traditional Django and then extend it into a web API with Django REST Framework.