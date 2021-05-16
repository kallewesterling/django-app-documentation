# Pull latest updates into production

## Step 1. Open a SSH tunnel

Open a SSH tunnel to dhinstitutes.org

```sh
$ ssh dhinstit@dhinstitutes.org
```

Login with the current login credentials.

## Step 2. Activate the environment

The curriculum website lives in its own virtual environment by default, which needs to be activated:

```sh
$ source virtualenv/curriculum.dhinstitutes.org/3.7/bin/activate
```

## Step 3. Navigate into the correct directory

Since the curriculum website is a subdomain, it lives inside a folder in the user root. Navigate into the directory:

```sh
$ cd curriculum.dhinstitutes.org
```

## Step 4. Pull

Make sure you're in the correct branch (you can check using `git status` which should provide you with the information that you're on the `v1-dev` branch, our current production branch).

??? note "Optional: Pulling from other development branch"

    The example above will always pull from the default branch.

    If you want to test run a new/different/updated development branch (for instance, if you're working on an issue and want to see it work in production), you would, after step 4 above, checkout a specific brand (in the example below, `v1-dev`):

    ```console
    $ git checkout --track origin/v1-dev
    ```

Now, you can pull the latest commits from GitHub:

```sh
$ git pull
```

## Step 5. Collect static files

All our static files are served by the static.dhinstitutes.org server, a different subdomain. We want to make sure all the static files are collected there before we restart the app:

```sh
$ python manage.py collectstatic
```

!!! important

    You will be asked whether you want to overwrite existing files. The answer is **yes**, which you will need to type.

Afterwards, you will want to [restart the Django app](restart.md) to make sure changes are done.
