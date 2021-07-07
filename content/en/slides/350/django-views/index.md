---
title: Django View Functions
summary: Explains how Django view functions work and how to use them
authors: []
tags: [isom350]
categories: []
date: "2021-05-02T20:46:46Z"
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

## Reminder of Django's MVT Model

Main components in a Django web application are:

1. **Models:** To handle data
2. **Views:** To handle business logic
3. **Templates:** To handle how screens will look

This organization enables team collaboration and specialization 

---

## Django Application Views

- A view refers to the webpage in a web application that implements a functionality
  - For example, login, cart, payment, catalog, and blog list screens.
- A view function is that function that is used to constructs the view in response to the browser requesting it
- It brings together the data performs the actions necessary to construct the page to be sne to the browser

---

## Building A View

The required tasks to build a view are:

1. Create the view function in your app's views.py
2. Link the view function to a path in root urls.py
3. (Optional) Prepare the template that has the design of the page

Data handling is done as part of creating the view function.

---

## View Functions

- Receive HTTP requests
- Perform a task
- Then return an HTTP response

---

## Understanding The View Function

In your app views.py:

```python
def test_view(request):
  print(f"Request: {request}")
```

---

## Continue With test_view

Now link the view function to a url path:

Update mysite/urls.py:

```python
from django.contrib import admin
from django.urls import path
from blog.views import test_view

urlpatterns = [
    path('admin/', admin.site.urls), 
    path('test/', test_view),    
]
```

---

## Test The New View

- Run the Django development server and you will notice:

{{< figure src="django-404.png" >}}

---

## What is Django Telling you?

1. 404 is a standard HTTP response code, it means that page you requested does not exist
   - Which page is that?
2. The available paths are `/admin/` and `/test/`
   - Where were they defined?
   - how can we fix the 404? do we need to?
   - How do we run our test_view?
---

## Continue Test The New View

- Point your browser to the path /test
- You need to pay attention to the output in two places:
  1. The browser
  2. The console (on replit.com)

---

{{< figure src="django-view-error.png" caption="What is this browser output telling us?" >}}

---

{{< figure src="django-console-error.png" caption="What is this console output telling us?" >}}

---

## Continue Test The New View

- Can you explain what just happened?
- How can we fix the ValueError?

---

## Solution

If your response was:
  
  Let `test_view` return an HTTP Response

Then you are correct!

---

## Fixing test_view

```python
from django.http import HttpResponse

def test_view(request):
  return HttpResponse("Hello World!")
```

---

## But What About HTML?

- Browsers are capable of rendering HTML
- Include HTML in the HttpResponse

```python
from django.http import HttpResponse

def test_view(request):
  return HttpResponse("""<html><body>
  <h1>Hello World!</h1>
  <p>This is my first <strong>html</strong> web app!</p>
  </body></html>""")
```

---

## FStrings Can Make HTML Dynamic

```python
from django.http import HttpResponse

def test_view(request):
  
  name = "ISOM 350 Student"

  return HttpResponse(f"""<html><body>
  <h1>Hello {name}!</h1>
  <p>This is my first <strong>html</strong> web app!</p>
  </body></html>""")
```

---

### User input will be a future topic

See forms


---

### Of course, we will not be writing HTML using Python Strings.

This is where Django Templates are most useful

---

### Summary

To create a fully functional web page in Django you need:

1. Create a view function to service this page
2. Create a path for the function in urls.py
3. Prepare the template for the page

Models will be used only if databases are needed and will be accessed from the view function.