# Setting environment variables

## Which ones are they?

The app requires four environment variables to be set in your environment:

| Variable    | Description                          |
| ----------- | ------------------------------------ |
| `SECRET_KEY`  | Django's own secret keys, which you can read more about [here](https://humberto.io/blog/tldr-generate-django-secret-key/) |
| `EMAIL_HOST_USER`  | Username for login to the email host |
| `EMAIL_HOST_PASSWORD`  | Password for login to the email host |
| `GITHUB_TOKEN`  | GitHub token to use for Markdown conversion |

## Backup solution

If you are not able to set environment variables correctly, there is a built-in backup solution.

### Step 1. Create the folder

Inside the `app` folder, create another empty folder called `.secrets`.

### Step 2. Create files

In the `.secrets` folder, place each of the environment variables as a file, with _only_ the variable in each file:

```
app
    |-- .secrets
        |-- SECRET_KEY
        |-- EMAIL_HOST_USER
        |-- EMAIL_HOST_PASSWORD
        |-- GITHUB_TOKEN
```

!!! important

    Note: No file ending should exist on these files
