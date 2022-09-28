# Session 1

To create a new **Django** project we first have to set up the (virtual) enironment:

1. install the **virualenv** package:
   ```
   py -m pip install virtualenv
   ```

2. create and start a new virtual env:
   ```
   py -m venv virtualenv_name
   virtualenv_name\Scripts\activate
   ```

3. install Django in that venv:
   ```
   pip install django
   ```

4. create a new Django project:
   ```
   django-admin startproject project_name
   ```

5. run the dev server through:
   ```
   python manage.py runserver
   ```
   basically, **manage.py** is the django-admin of a specific project

---

after creating the new project our folder structure will be:
```
mysite
|
|   db.sqlite
|   manage.py
└───mysite
|    |
|    |   asgi.py
|    |   wsgi.py
|    |   settings.py -> your project's settings
|    |   urls.py     -> pretty obvious
|
└───
```

Django consists of *apps*, they make up the whole project. (probably like components in react)

to create new apps(modules?)

1. we run:
  ```
    python manage.py startapp app_name
  ```

2. then add a *urls.py* file to the newly created app

3. configure the main *urls.py* to point to the new app (read the comments, theyr), and also add the app to **INSTALLED_APPS** list in **settings.py**

# TBC

---
# Session 2
## Django Templating Language (DTL)

- use **{{value}}** to use a value from the context dictionary
- **Filters**: [view them here](https://www.djangotemplatetagsandfilters.com/)
  ```
    <h1> {{value}} | filter  </h1>
    <h1> {{value}} | default: default_value  </h1> -> prints default value if value is not available
    <h1> {{value}} | slice:'4:7'  </h1> -> Returns a slice of a sequence.
    <h1> {{value}} | length  </h1> -> prints length of value
    <h1> {{value}} | add: 'whatever string you want' </h1> -> concatenates strings
    <h1> {{value}} | cut: 'x'  </h1> -> removes all x charachters from value
    <h1> {{value}} | cut: 'x' | capfirst  </h1> -> removes x charachters and capitalize (multiple filters)
    <h1> {{file_size_value}} | filesizeformat  </h1> -> transforms number into readable filesize
  ```

- **Tags**: {% tag %} {% endtag %}
  ```
    {% comment %} for comments obviously {% endcomment %}

  ```

- we can create a **base template** to include stuff like footers and navbars that will be on every template
    1. create a **base.html** in the base templates directory
    2. in new templates use **{% extends base.html%}**
   so basically we can create reusable template components. yay.

- create blocks and name them to be able to re-use them in differnet template
  ```
    {% block blockname %} {% endblock blockname %}
  ```
- use **include** tag to i n c l u d e a component like a navbar
  ```
  {% include "footer.html" %}
  ```