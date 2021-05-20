# Deploy on Reclaim Cloud (draft)

Note that these are not finished installation instructions.

<!-- TODO: add finished instructions -->

## Step 1. Create environment and deploy the GitHub repository into the cloudlet.

## Step 2. Make sure that the virtual environment exists

```sh
$ cd ~
```

```sh
$ virtualenv virtenv
```

```sh
$ source virtenv/bin/activate
```

```sh
$ pip install -r ROOT/requirements.txt
```

## Step 3 (I believe this is necessary...): edit webroot/virtenv/bin/activate_this.py

below `os.environ["VIRTUAL_ENV"] = base`, add the following:

```py
os.environ["SECRET_KEY"] = '<insert secret key>'
os.environ["EMAIL_HOST_USER"] = '<insert email username>'
os.environ["EMAIL_HOST_PASSWORD"] = '<insert email password>'
os.environ["GITHUB_TOKEN"] = '<insert github token>'
```

## Step 4 (I believe this is necessary): webroot/virtenv/bin/activate

below `PATH="$VIRTUAL_ENV/bin:$PATH"` and `export PATH`, add the following:

```bash
export SECRET_KEY='<insert secret key>'
export EMAIL_HOST_USER='<insert email username>'
export EMAIL_HOST_PASSWORD='<insert email password>'
export GITHUB_TOKEN='<insert github token>'
```

## Step 5: Edit /etc/httpd/conf.d/wsgi.conf

It should look like this:

```conf
Protocols h2 h2c http/1.1

WSGIDaemonProcess apache user=apache group=apache processes=2 threads=10 python-path="/var/www/webroot/virtenv/lib/python/:/var/www/webroot/" home="/var/www/webroot/"

ServerRoot "/var/www/webroot/"
DocumentRoot "/var/www/webroot/"
User apache
Group apache

DefaultRuntimeDir "/var/run"

ErrorLog "/var/log/httpd/error_log"
CustomLog "/var/log/httpd/access_log" combined

<Directory "/var/www/webroot/">
AllowOverride all
Options -MultiViews
</Directory>

Alias /robots.txt /var/www/webroot/ROOT/robots.txt
Alias /favicon.ico /var/www/webroot/ROOT/favicon.ico
#Alias /images /var/www/webroot/ROOT/images
#Alias /static /var/www/webroot/ROOT/static
Alias /.well-known /var/www/webroot/ROOT/.well-known

#WSGIScriptAlias / ${WSGI_SCRIPT}
WSGISocketPrefix "/tmp/wsgi"
WSGIPassAuthorization On
#WSGIProcessGroup apache

WSGIScriptAlias / /var/www/webroot/ROOT/app/wsgi.py
WSGIPythonHome /var/www/webroot/.virtualenvs/env2
WSGIPythonPath /var/www/webroot/ROOT

<Directory /var/www/webroot/ROOT/app>
<Files wsgi.py>
Order deny,allow
Allow from all
</Files>
</Directory>

Alias /media/ /var/www/webroot/ROOT/media/
Alias /static/ /var/www/webroot/ROOT/static/

<Directory /var/www/webroot/ROOT/static>
Order deny,allow
Allow from all 
</Directory>

<Directory /var/www/webroot/ROOT/media>
Order deny,allow
Allow from all
</Directory>
```

## Step 6: Restart `httpd`

```sh
$ sudo service httpd restart
```