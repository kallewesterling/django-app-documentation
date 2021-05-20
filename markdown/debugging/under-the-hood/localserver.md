# The `localserver` command explained

Essentially the `localserver` command is [Django's native `runserver`](https://docs.djangoproject.com/en/3.2/ref/django-admin/#runserver) disguised with some specific settings. It runs with the IP address `0.0.0.0` on port `80` with [ALLOWED_HOSTS](https://docs.djangoproject.com/en/3.2/ref/settings/#allowed-hosts) having `'*'` as a value, in case it wasn't already there.

The code, specifically, looks like this;

```py
settings.ALLOWED_HOSTS.append('*')
args = ['name', 'runserver', '0.0.0.0:80']
execute_from_command_line(args)
```
