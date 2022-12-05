# __Django Custom User__

## Django Best Practices: Custom User Model

Django ships with a built-in User model for authentication and if you'd like a basic tutorial on how to implement log in, log out, sign up and so on see the Django Login and Logout tutorial for more.

## Setup

To start, create a new Django project from the command line. We need to do several things:

- create and navigate into a dedicated directory called accounts for our code

- install Django
- make a new Django project called django_project
- make a new app accounts
- start the local web server

Here are the commands to run:

    # Windows
    > cd onedrive\desktop\code
    > mkdir pages
    > cd pages
    > python -m venv .venv
    > .venv\Scripts\Activate.ps1
    (.venv) > python -m pip install django~=4.0.0
    (.venv) > django-admin startproject django_project .
    (.venv) > python manage.py startapp accounts
    (.venv) > python manage.py runserver

    # macOS
    % cd ~/desktop/code
    % mkdir pages
    % cd pages
    % python3 -m venv .venv
    % source .venv/bin/activate
    (.venv) % python3 -m pip install django~=4.0.0
    (.venv) % django-admin startproject django_project .
    (.venv) % python3 manage.py startapp accounts
    (.vent) % python3 manage.py runserver

## AbstractUser vs AbstractBaseUser

There are two modern ways to create a custom user model in Django: AbstractUser and AbstractBaseUser. In both cases we can subclass them to extend existing functionality however AbstractBaseUser requires much, much more work. Seriously, don't mess with it unless you really know what you're doing. And if you did, you wouldn't be reading this tutorial, would you?

So we'll use AbstractUser which actually subclasses AbstractBaseUser but provides more default configuration.

