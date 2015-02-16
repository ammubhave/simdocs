---
title: Sample Reference

language_tabs:
  - shell
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

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
