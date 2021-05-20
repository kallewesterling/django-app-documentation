# File structure explained

[Django's own tutorial](https://docs.djangoproject.com/en/3.2/intro/tutorial01/#creating-a-project) does a good job of explaining the basic structure of a Django project. If you haven't worked in Django before, it is well worth a read. In this file, I want to detail some important folders and files in the `django-app` directory for developers.

## `app` directory

This is an important directory as it contains all the central Django files, most centrally `settings.py`, which defined a lot of the project's basic set-up, such as which apps are installed.

### `settings.py` file

Importantly, the `settings.py` file contains the algorithm that reads in the `SECRET_KEY` environment variable (with the backup solution of reading it from the file).

It also contains the [`DEBUG`](../../settings/debug-mode.md) setting, which should be turned to `False` but is currently (in our alpha-dev stage) still set to `True`, which exposes us to some security risks.

It also contains the `TEMPLATES['DIRS]` variable, which ensures that all our templates can be located in the `templates` directory in the root of the repository.

The `settings.py` file is also what defines the MySQL settings, once we want to move ahead with setting mySQL as the backend database solution rather than the `sqlite` file that currently serves as our database.

This is also where you'll find the `STATICFILE_DIRS`