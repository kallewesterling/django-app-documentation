# Keeping up-to-date: Synchronizing Database with GitHub Repositories

!!! note "When you should follow these instructions"
    The instructions below should be followed _after_ you have made edits to any of the curriculum website's linked repositories.

## 1. Make sure you are in the root of the Django app

```sh
$ cd /path/to/django-app/
```

## 2. Mirror the live data: `build`

The first thing we want to do is make a mirrored copy of all of the data that lives in the GitHub repositories related to the DHRI curriculum. We can do so with the build `shortcut` command:

```sh
$ python manage.py build
```

If you need a reminder or want to read more about this command and what is happening in this step on the [Populating the Database page](2-populating-the-database.md).

## 3. Ingest the data from your local files: `ingest`

In this step, we want to ingest the mirrored copy of all of the data that lives in the GitHub repositories, downloaded and structured in Step 1. We can do so with the `ingest` shortcut command:

```sh
$ python manage.py ingest
```

!!! tip

    Now that you have finished keeping the database up to date, don't forget to [keep the GitHub files up to date as well](building-backup-content.md).
