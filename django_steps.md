# Django Setup in Windows & VS Code (Python v 3)

## Project Creation

01. Create a project folder (Ex. btre_project) in your local machine.
02. Open **THE PROJECT** in VS Code.
03. Create a .gitignore file in project root (No need if there it is)
04. Go to [gitignore.io](https://www.gitignore.io/) and select the gitignore file for django. Copy & paste it in your gitignore file.

## Virtual Environment Setup

01. Open bash terminal in VS Code. (Asume that your computer has intalled [git bash](https://git-scm.com/downloads))
02. Type `pip freeze` to check the installed global packages. (*Optional*)
03. Type `python -m venv ./venv` to create a virtual environment in current directory.

## Virtual Environment Activate / Deactivate

01. Type `source venv/Scripts/activate` to activate the virtual environment.
02. Type `deactivate` to deactivate the virtual environment.

## Django Installation

01. Activate the virtual environment. (No need If you are already in the virtual environment)
02. Type `pip install django` to install django.
03. Type `pip freeze` to view all the installed packages.

## Aditional Installation

01. Activate the virtual environment. (No need If you are already in the virtual environment)
02. Type `pip install pylint` to install pylint.
02. Type `pip install autopep8` to install autopep8.

## Project Creation (in Django)

01. Activate the virtual environment. (No need If you are already in the virtual environment)
02. Type `django-admin startproject your_project_name .` to create a project. ( . is used for the current directory)
03. Type `python manage.py runserver` to run the localhost server.
04. Access your server in any browser at **localhost:8000**.

## Template Creation (in Django)

01. Create a folder called `templates` in the project root.
02. Define the templates location in settings.py => TEMPLATES => `'DIRS': [os.path.join(BASE_DIR, 'templates')]`
03. Create a HTML file called `base.html` in templates folder.
04. Include follwing between body tag

```jinja
{% block content %} {% endblock %}
```

05. Include `{% load static %}` in base.html before the DOCTYPE.
06. Include follwings in every **TEMPLATE HTMLs**.
```jinja
{% extends 'base.html' %}

{% block content %}
    <h1>Any html content goes here</h1>
{% endblock %}
```

07. Create a folder called `partials` in template folder.
08. Create seperate HTML files for diffrent partial items inside the `partials` folder. Ex. "_navbar.html" for navbar partial
09. Include your partials using `{% include 'partials/_navbar.html' %}` in any HTML file.

## Collect Statics Files (in Django)

01. Create a folder called `static` in `your_project_name` folder.
02. Create `css`, `js`, `webfonts`, `img` folders inside static folder. and put related resources to related folders.
03. Add the following code to settings.py

```python
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'your_project_name/static')
]
```
04. Run `python manage.py collectstatic` in VS Code terminal.
05. Wrap your all static links in base.html using `{% static 'location/to file' %}`
```html
Before:
<!-- Theme CSS -->
<link href="../css/main-style.css" rel="stylesheet" type="text/css">

After:
<!-- Theme CSS -->
<link href="{% static 'css/main-style.css' %}" rel="stylesheet" type="text/css">
```

## Create Apps (in Django)

01. Activate the virtual environment. (No need If you are already in the virtual environment)
02. Type `python manage.py startapp your_app_name`
03. Go to project folder => settings.py => INSTALLED_APPS & add `app_name.apps.App_NameConfig`.
04. Open `views.py` located in `your_app_name` folder & include the following code.

```python
from django.shortcuts import render

def index(request):
    return render(request, 'path/to index.html')
```
05. Create a file called `urls.py` in `your_app_name` folder & include the following code & save.

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.view_method, name='view_name')
    #   Ex. path('', views.index, name='index') //for index.html
    #       path('about', views.about, name='about')
    #       path('<int:listing_id>', views.listing, name='listing') //for dynamic links
]
```
06. Include the following code in `urls.py` in `your_app_name` folder folder & save
```python
path('your_app_name/', include('your_app_name.urls')),
path('admin/', admin.site.urls),
```
