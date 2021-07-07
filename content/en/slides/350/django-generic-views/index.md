---
title: Django Generic Views
summary: Add quick and easy CRUD functionality to your web application
authors: []
tags: [isom350]
categories: []
date: "2021-05-12T12:07:11Z"
draft: True
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

Django View Functions

---

## Django MVT Webapp Model

When constructing webapps, we build:

1. **Models:** To handle data
2. **Views:** To handle business logic
3. **Templates:** To handle how screens will look

We continue to work on models, views, and templates as we build a webapp

---

## Django Simplification of CRUD Functionality

- Most functions in a data-driven web app are CRUD operations
- We can reuse some ready made generic Django views for CRUD operations
  - We just have to configure them
- Alternatively, we can write the whole view function as we have learned previously
  
---

## The Read Operation

Such operations are used to retrieve data from the database, then display it as:
1. A list
2. A single object

---

## For Single Objects

1. Subclass `DetailView` from `django.views.generic`
2. Define the `model` to use 
3. Define the `template_name`

---

## For Single Objects


```python
from django.views import generic
from .models import Post


class PostDetailView(generic.DetailView):
  model = Post
  template_name = 'post_detail.html'
```


---

## For List Views

1. Subclass `ListView` from `django.views.generic`
2. Define what list to show using `queryset` 
3. Define the `template_name`

---

## The List View

```python
from django.views import generic
from .models import Post


class PostListView(generic.ListView):
  queryset = Post.objects.filter(status=1).order_by('-created_on')
  template_name = 'post_list.html'
```

---

Can you tell what is missing to complete this web app?

---

## The Missing Parts (need to add this)

1. Creating a url path for each view
2. Providing the templates
