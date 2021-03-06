# upload-and-update-django-project-on-heroku

<!-- Project Upload -->
Configuring Django Apps for Heroku

First, and most importantly, Heroku web applications require a Procfile.

# This file is used to explicitly declare your application’s process types and entry points. It is located in the root of your repository.

Procfile.py --->
```python
web: gunicorn myproject.wsgi
```

<code>$ pip install gunicorn</code>

<code>$ pip install django-heroku</code>

<code>$ pip freeze > requirements.txt</code>


# Add the following import statement to the top of settings.py:
```python
import django_heroku
```

# Then add the following to the bottom of settings.py:
```python
# Activate Django-Heroku.
django_heroku.settings(locals())
```

# Add this in settings.py-->
```python
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

** PS: if Heroku isn't recognized as a command, please close your terminal and editor and then re-open it.

DEBUG = False # in settings.py

ALLOWED_HOSTS = ['your_app_name.herokuapp.com', 'localhost', '127.0.0.1'] # in settings.py
```

# New project upload command -->
<code>$ git init</code>

<code>$ git add .</code>

<code>$ git commit -m "first commit"</code>

<code>$ heroku login</code>

<code>$ heroku create app_name</code>

<code>$ heroku config:set DISABLE_COLLECTSTATIC=1</code>

<code>$ git push heroku master</code>

<code>$ heroku run python manage.py migrate</code>

# Create super user -->
<code>$ heroku run:detached python manage.py createsuperuser</code>

# Project Update -->
<code>$ heroku login</code>

<code>$ heroku git:remote -a app_name</code>

<code>$ git add .</code>

<code>$ git commit -am "make it better"</code>

<code>$ git push heroku master</code>

# Model Migrate -->
<code>heroku run python manage.py migrate</code>
