# Dropping all migration files

This might be needed to run during dev time:

```sh
$ find . -path "*/migrations/*.py" -not -name "__init__.py" -delete && find . -path "*/migrations/*.pyc"  -delete && git pull
```
