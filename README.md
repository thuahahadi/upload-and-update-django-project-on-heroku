# upload-and-update-django-project-on-heroku

<!-- Project Upload -->
Configuring Django Apps for Heroku

First, and most importantly, Heroku web applications require a Procfile.

# This file is used to explicitly declare your application’s process types and entry points. It is located in the root of your repository.

Procfile.py --->
web: gunicorn myproject.wsgi

$ pip install gunicorn
$ pip install django-heroku

$ pip freeze > requirements.txt

# Add the following import statement to the top of settings.py:
import django_heroku

# Then add the following to the bottom of settings.py:
# Activate Django-Heroku.
django_heroku.settings(locals())

# Add this in settings.py-->
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

<!-- New project upload command -->
$ git init
$ git add .
$ git commit -m "first commit"
$ heroku login
$ heroku create app_name
$ heroku config:set DISABLE_COLLECTSTATIC=1
$ git push heroku master
$ heroku run python manage.py migrate

<!-- Create super user -->
$ heroku run:detached python manage.py createsuperuser

<!-- Project Update -->
$ heroku login
$ heroku git:remote -a app_name
$ git add .
$ git commit -am "make it better"
$ git push heroku master

<!-- Model Migrate -->
heroku run python manage.py migrate
