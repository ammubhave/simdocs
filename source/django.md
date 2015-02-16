---
title: Getting Started with Django

search: true
---

# Introduction

Simmons Admin Dashboard supports Django websites using WSGI.

# How to deploy

## .htaccess

Create a .htaccess file in your root directory.

```shell
AddHandler wsgi-script .py
Options +ExecCGI

RewriteEngine On
RewriteBase /PATH

RewriteRule ^(static.*)$ - [L]

RewriteCond %{REQUEST_URI} ^/PATH/$
RewriteRule ^$ APP_NAME/wsgi.py [L]

RewriteCond %{REQUEST_URI} !/PATH/APP_NAME/wsgi.py
RewriteRule ^(.*)$ APP_NAME/wsgi.py/$1 [L]
```

## APP_NAME/settings_local.py

Create a copy of `settings.py` as `settings_local.py`. This file will be your local settings configuration.

## manage.py

Change the line `os.environ.setdefault("DJANGO_SETTINGS_MODULE", "APP_NAME.settings")` to `os.environ.setdefault("DJANGO_SETTINGS_MODULE", "APP_NAME.settings_local")`

## APP_NAME/wsgi.py

Add these lines right after the settings import

```python
import sys
sys.path.append(os.path.dirname(os.path.dirname(__file__)))
```

# Authentication

> To allow access to only MIT users add this to .htaccess:

```
SSLVerifyClient require
```

> To only allow access to a admins, add:

```
SSLOptions +FakeBasicAuth +StdEnvVars

AuthUserFile /var/www/apache_config/simadmin/.htpasswd
AuthName "APP NAME Authentication"
AuthType Basic
Require valid-user
AuthBasicProvider file
```