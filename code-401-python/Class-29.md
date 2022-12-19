# __API Deployment__

## Configuring Django Settings: Best Practices

This article is intended for engineers who use the Django framework. It gives a deep insight into configuring Django project settings, and the pros and cons of different approaches.

In the article, you will also find recommendations concerning tools, best practices, and architectural solutions, all time-tested and proven by successful projects. And if you still have questions after reading it, you can always leave a comment below or use our contact form. The article is based on Django Stars’ vast experience with real projects. Our dedicated teams are ready to speed up your development project.

---

## Setting Django Configurations: Different Approaches

There is no built-in universal way to configure Django settings without hardcoding them. But books, open-source and work projects provide a lot of recommendations and approaches on how to do it best. Let’s take a brief look at the most popular ones to examine their weaknesses and strengths.

### __settings_local.py__

This is the oldest method. I used it when I was configuring a Django project on a production server for the first time. I saw a lot of people use it back in the day, and I still see it now.

The basic idea of this method is to extend all environment-specific settings in the settings_local.py file, which is ignored by VCS. Here’s an example:

__settings.py file:__

    ALLOWED_HOSTS = ['example.com']
    DEBUG = False
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'production_db',
            'USER': 'user',
            'PASSWORD': 'password',
            'HOST': 'db.example.com',
            'PORT': '5432',
            'OPTIONS': {
                'sslmode': 'require'
            }
        }
    }

    ...

    from .settings_local import *

__settings_local.py file:__

    ALLOWED_HOSTS = ['localhost']
    DEBUG = True
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'local_db',
            'HOST': '127.0.0.1',
            'PORT': '5432',
        }
    }

### Pros:
* Secrets not in VCS.

### Cons:
* settings_local.py is not in VCS, so you can lose some of your Django environment settings.
* The Django settings file is a Python code, so settings_local.py can have some non-obvious logic.
* You need to have settings_local.example (in VCS) to share the default Django configurations for developers.

---

## Separate settings file for each environment

This is an extension of the previous approach. It allows you to keep all configurations in VCS and to share default settings between developers.

In this case, there are multiple files from which projects on Django get settings, and you make a settings package with the following file structure:

    settings/
    ├── __init__.py
    ├── base.py
    ├── ci.py
    ├── local.py
    ├── staging.py
    ├── production.py
    └── qa.py

__settings/local.py:__

    from .base import *


    ALLOWED_HOSTS = ['localhost']
    DEBUG = True
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'local_db',
            'HOST': '127.0.0.1',
            'PORT': '5432',
        }
    }

To specify for a project you run which Django configuration to use, you need to set an additional parameter:

    python manage.py runserver --settings=settings.local

### Pros:
* All environments are in VCS.
* It’s easy to share settings between developers.

### Cons:
* You need to find a way to handle secret passwords and tokens.
* “Inheritance” of settings can be hard to trace and maintain.

### Environment variables

To solve the issue with sensitive data, you can use environment variables in Django.

    import os


    SECRET_KEY = os.environ['SECRET_KEY']
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': os.environ['DATABASE_NAME'],
            'HOST': os.environ['DATABASE_HOST'],
            'PORT': int(os.environ['DATABASE_PORT']),
        }
    }

This is the simplest example using Python os.environ and it has several issues:

1. You need to handle KeyError exceptions.
2. You need to convert types manually (see DATABASE_PORT usage).

To fix KeyError, you can write your own custom wrapper. For example:

    import os

    from django.core.exceptions import ImproperlyConfigured


    def get_env_value(env_variable):
        try:
            return os.environ[env_variable]
        except KeyError:
            error_msg = 'Set the {} environment variable'.format(var_name)
            raise ImproperlyConfigured(error_msg)


    SECRET_KEY = get_env_value('SECRET_KEY')
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': get_env_value('DATABASE_NAME'),
            'HOST': get_env_value('DATABASE_HOST'),
            'PORT': int(get_env_value('DATABASE_PORT')),
        }
    }


Also, you can set default values for this wrapper and add type conversion. But actually there is no need to write this wrapper, because you can use a third-party library (we’ll talk about this later).

### Pros:
* Django config is separated from code.
* Environment parity – you have the same code for all environments.
* No inheritance in settings, and cleaner and more consistent code.
* There is a theoretical grounding for using Django environment variables – 12 Factors.
### Cons:
* You need to handle sharing default config between developers.