---
title: Improved URLs
summary: How to improve the url path design of a Django web application and exploring some of the best practices.
authors: []
tags: [isom350]
categories: []
date: "2021-05-11T15:05:30Z"
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: moon
  # Choose a code highlighting style (if highlighting enabled in `params.toml`)
  #   Light style: github. Dark style: dracula (default).
  #   Available highlight themes listed in: https://highlightjs.org/static/demo/
  #   Use lower case names and replace space with hyphen '-'
  highlight_style: dracula

  diagram: true
  diagram_options:
    # Mermaid diagram themes include: default,base,dark,neutral,forest
    theme: dark

  # RevealJS slide options.
  # Options are named using the snake case equivalent of those in the RevealJS docs.
  reveal_options:
    controls: true
    progress: true
    slide_number: c/t  # true | false | h.v | h/v | c | c/t
    center: true
    rtl: false
    mouse_wheel: true
    transition: concave  # none/fade/slide/convex/concave/zoom
    transitionSpeed: default  # default/fast/slow
    background_transition: slide  # none/fade/slide/convex/concave/zoom
    touch: true
    loop: false
    menu_enabled: true
    chalkboard_enabled: true
    history: true
---


# ISOM 350
## Business Application Development

Mohammad AlMarzouq

Improved URLs

---

## URL Paths

- It's a good idea to make them readable
- Can be static:
```
/blog/posts
```

- Or Dynamic (known as URL Patterns):
```
/blog/post/10
/blog/post/234
/profile/khaled
/profile/ahmed
```

---

## Defining URL Paths

- Done in mysite/urls.py
- We add Paths to the urlpatterns list
- Each Path links a URL path to a view function:
```python
urlpatterns = [ 
    path('test/', test_view),   
    path('blog/post', blog_posts),   
]
```
Remember to import the view functions!

---

## Defining Dynamic Paths

- Place them in the urlpatterns list
- Example dynamic paths:
```python
path('profile/<str:name>/', user_profile),
path('blog/post/<slug:slug>/', view_post_by_slug),
path('blog/post/<int:id>/', view_post_by_id),
path('blog/post/<int:year>/<int:month>/', view_posts_in_month),
```

---

## Defining Variable in URL Paths

The syntax:
```
<data_type:variable_name>
```
Just place it in the part that you would like to vary in the URL path

---

## View Functions with Dynamic Paths

- For every variable in the URL path, the linked view function must have a matching argument that match the variable name
- For example, the following path:
```python
path('profile/<str:name>/', user_profile),
```
Must be matched with the following view function:
```python
def user_profile(request, name):
```

---

## Another Matching Example

The following path:
```python
path('blog/post/<int:year>/<int:month>/', view_posts_in_month),
```
Must be matched with the following view function:
```python
def view_posts_in_month(request, year, month):
```

---

## Improved URL Organization

- Look at the admin urls:

```python
path('admin/', admin.site.urls), 
```

- What is `admin.site.urls`?
- It is not a view function, but the url paths for the admin interface
- Similarly, we can define URL paths in our app directory

---

## Defining URLS Inside an APP

- Create a urls.py inside the blog app
- in the root urls.py (mysite/urls.py):
  - import the include function from django.urls
  - use include to point to the urls in your app

---

## The Improved Root urls.py

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),   
    path('blog/', include('blog.urls')),
]
```
This is telling Django that our paths can be found in the blog app in the file named urls.py

---

## The blog prefix

- One important thing to keep in mind, that all the blog app urls will start with /blog
- because of this line:
```python
path('blog/', include('blog.urls')),
```
- If the URL path starts with /blog/, then the rest of the path can be processed according to blog/urls.py

---

## blog/urls.py

```python
from . import views
from django.urls import path

urlpatterns = [
    path('', views.post_list),
    path('<slug:slug>/', views.display_post),
]
```
Notice we do not execute the function using ()

---

## Why Are URL Path Variable Important?

- Allows for selection of specific items or ranges in our data
- Considered a user input method

---

## How Can URLs Be Used for Input?

- Let's improve our test_view function to:
  1. Define the urls in blog/urls.py
  2. Set the name of the person to greet from url, /greet/mohammad will result in the message "hello mohammad"

---

## Root urls.py:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),   
    path('blog/', include('blog.urls')),
]
```

--- 

## blog/urls.py

```python
from . import views
from django.urls import path

urlpatterns = [
    path('greet/<str:name>', views.test_view),
]
```

---

## blog/views.py

```python
def test_view(request, name):
  data = {}
  data["name"] = name
  return render(request, 'test.html', context=data)
```

---

## blog/templates/test.html

```html
<html>
  <body>
  <h1>Hello {{ name }}!</h1>
</html>
```

---

- Now how can you access the view from the browser?

---

The correct path is:
```
/blog/greet/your-name-here
```

As you change the name part in the path, so will the message in the page

---

- This understanding of URLs will be important for the next part of working with data.
- Please read the [URL dispatcher documentation](https://docs.djangoproject.com/en/3.2/topics/http/urls/) for more information.

---

## Final Note on URLs

- It is good practice to give unique names for URLs in Django
- Will allow you to avoid hard-coding urls in your web app
- An excellent explanation is provided in the [django documentation](https://docs.djangoproject.com/en/3.2/intro/tutorial03/#removing-hardcoded-urls-in-templates)
