# Pull latest updates into production

In a Terminal:

1. Open a SSH tunnel to dhinstitutes.org
    ```sh
    $ ssh dhinstit@dhinstitutes.org
    ```

2. Activate the environment:
    ```sh
    $ source virtualenv/curriculum.dhinstitutes.org/3.7/bin/activate
    ```

3. Navigate into the directory:
    ```sh
    $ cd curriculum.dhinstitutes.org
    ```

4. Pull:
    ```sh
    $ git pull
    ```

5. Collect all the static files in the static.dhinstitutes.org server:
    ```sh
    $ python manage.py collectstatic
    ```

    _You will be asked whether you want to overwrite existing files. The answer is **yes**._

Afterwards, you may want to [restart the Django app](restart.md) to make sure changes are done.

---

## Optional: Pulling from other development branch

The example above will always pull from the default branch.

If you want to test run a new/different/updated development branch (for instance, if you're working on an issue and want to see it work in production), you would, after step 4 above, checkout a specific brand (in the example below, `v1-dev`):

```console
$ git checkout --track origin/v1-dev
```
