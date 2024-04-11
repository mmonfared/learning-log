## Learning Log Web Application 

We’ll write a web app called Learning Log that allows users to
log the topics they’re interested in and to make journal entries as
they learn about each topic. The Learning Log home page will
describe the site and invite users to either register or log in. Once
logged in, a user can create new topics, add new entries, and read
and edit existing entries.

### Quick Note:
`python -m venv venv` # create python environment

`source venv/bin/activate` # activate python env

`pip install django` # install django

`django-admin startproject project-name .` # create django project

`python manage.py migrate` # initialize database

`python manage.py runserver` # to view the project

`python manage.py startapp app-name` # create app

// Add models > add app to setting (INSTALLED list) > import model to admin.py

`python manage.py makemigrations app-name` # create migrations for app

`python manage.py migrate` # migrate database

`python manage.py createsuperuser` # to create admin 

`python manage.py shell` # open django shell 

// >>> from app-name.models import ModelName

// >>> ModelName.objects.all()

==== Add pages
1. Define URLs
   1.
        `learning_log/urls.py`
        ```python
        from django.contrib import admin
        from django.urls import path, include
        
        urlpatterns = [
            path('admin/', admin.site.urls),
            path('', include('learning_logs.urls'))
        ]
        ```
   2. `learning_logs/urls.py` (add new file)
      ```python
        """Define URLS patterns for learning_logs."""
        
        from django.urls import path
        
        from . import views
        
        app_name = 'learning_logs'
        urlpatterns = [
            # Home page
            path('', views.index, name='index')
        ]
        ```

2. Write Views

    `learning_logs/views.py`
    ```python
    from django.shortcuts import render

    def index(request):
     """The home page for Learning Log."""
        return render(request, 'learning_logs/index.html')
    ```

3. Writing Templates

    `learning_logs/templates/learning_logs/index.html` (create the nested directory like this)
    ```html
        <h2>Learning Log</h2>

        <p>Learning Log helps you keep track of your learning, for any topic you're learning about.</p>
    ```