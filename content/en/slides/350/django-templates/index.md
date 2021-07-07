---
title: Django Templates
summary: Using Django Temapltes to control web application look and feel
authors: []
tags: [isom350]
categories: []
date: "2021-05-11T15:02:06Z"
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

Django Templates

---

## Recap

So far, we have:

1. Created the view function `test_view`
2. Updated the root urls.py to set a path for `test_view`

---

## views.py

```python
from django.http import HttpResponse

def test_view(request):
  return HttpResponse("""<html><body>
  <h1>Hello World!</h1>
  <p>This is my first <strong>html</strong> web app!</p>
  </body></html>""")
```

---

## Root urls.py

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

## Let's Take Advantage of Templates

- Use the render function:
- Arguments we will use in order:
  1. The HTTP request
  2. The template file name
  3. The context (optional)

---

## Updated test_view Function

```python
from django.shortcuts import render

def test_view(request):
  return render(request, 'test.html')
```

---

## The Result

{{< figure src="django-template-error.png" >}}

Django cant find text.html

---

## The Solution

1. Inside the `poll` directory, create a new directory named `templates`
2. Inside the `temapltes` directory, create a new file named `test.html`
3. Edit `test.html` to look like this:

```html
<html>
  <body>
  <h1>Hello World!</h1>
  <p>This is my first <strong>html</strong> web app!</p>
  </body>
</html>
```

---

## Template Based Application

- The application works and looks the same
- It now separates HTML from Python code
  - HTML placed in templates
  - Python code in .py files
- To change how the application looks the designers edit test.html

---

## HTML Tags

Every HTML `<tag>` will have a matching closing `</tag>`
For example:
```html
<h1>heading 1</h1>
```
Tags can contain other tags:

```html
<div>
  <p>
  This is a paragraph inside a div
  </p>
</div>
```

---

- Some tags require specific tags inside them
- Like LI inside UL or OL tags:
```html
<ul>
  <li>item 1</li>
  <li>item 2</li>
</ul>
```

---

## Useful HTML Tags

- A for creating links (known as anchor)
- H1 to H4 for headings
- DIV for page sections, used to create structure
  - Example: Menu, header, footer, content ..etc
- P for paragraphs, used to divide textual content
- OL/UL for ordered/unordered lists and TABLE
- BR for line breaks, no closing tag, written as:

```html
<BR />
```

---

## Links (Anchors)

- Syntax:
```html
<a href="http://google.com">My Text</a>
```
- Will turn "My Text" into a link, if clicked will open google's homepage
- See [HTML anchor tag reference](https://www.w3schools.com/tags/tag_a.asp) for examples


---


## Ordered and Unordered lists

- OL for ordered lists
- UL for unordered lists
- LI used to include list items in both OL and UL

---

## Ordered List Example

```html
<OL>
  <LI>first item</LI>
  <LI>second item</LI>
</OL>
```
{{< figure src="django-template-ol.png" >}}


---

## Unordered List Example

```html
<UL>
  <LI>first item</LI>
  <LI>second item</LI>
</UL>
```
{{< figure src="django-template-ul.png" >}}


---

## HTML Table

- TABLE, must include:
  - TR for each row including, it includes either
    - Then place data for each column in a TH or TD tag:
      - TH to format data as a header cell
      - TD to format data as a data cell
    - Choice of TH or TD is mainly for formatting

---

## Table Example

```html
<TABLE>
  <TR>
    <TH>Column 1</TH>
    <TH>Column 2</TH>
  </TR>
  <TR>
    <TH>row 1 item 1 (header)</TH>
    <TD>row 1 item 2</TD>
  </TR>
  <TR>
    <TD>row 2 item 1</TD>
    <TD>row 2 item 2</TD>
  </TR>
</TABLE>
```

---

## Table Output

{{< figure src="django-template-table.png" >}}

---


## FORM Tag

- There is also an HTML FORM tag used for data submission
- We will cover that when discussing Django forms
- We will let Django construct forms for us as there are some security risks in building HTML forms manually

---

## Django Template Language

- Used to control some output behavior in templates
- Different syntax than python,
- Embedded in HTML and written inside special blocks {{ }} and {% %}
- [Django Template Language (DTL) documentation](https://docs.djangoproject.com/en/3.2/ref/templates/language/) is short and is a required reading

---

## Template Variables

- Variables are placed in a dictionary
- Pass the dictionary as context argument in render function
- Use {{ variable name }} to display content of variable

---

## Template Variable Example

```python
def test_view(request):
  data = {}
  data["name"] = "ISOM 350 Student"
  return render(request, 'test.html', context=data)
```

---

## Template Variable Example

```html
<html>
  <body>
  <h1>Hello {{ name }}!</h1>
  <p>This is my first <strong>html</strong> web app!</p>
  </body>
</html>
```

---

- Remember you can add as many variables as you like
- Just add a key-value pair for every variable, where:
  - key is the variable name
  - value is the variable value
- Try to add another variable and display it i nthe template

---

## Collections in Templates

```python
def test_view(request):
  data = {}
  data["name"] = "ISOM 350 Student"
  data["topics"] = ["python", "django", "views", "templates"]
  return render(request, 'test.html', context=data)
```

---

## For Loop In Templates

```html
<html>
  <body>
  <h1>Hello {{ name }}!</h1>
  <h2> Topics include:</h2>
  {% for t in topics %}
    {{ t }}
  {% endfor %}
</html>
```

---

## Output

{{< figure src="django-template-for.png" >}}

This is how HTML works, you have to specify new line.

---

```html
<html>
  <body>
  <h1>Hello {{ name }}!</h1>
  <h2> Topics include:</h2>
  {% for t in topics %}
    {{ t }} <br />
  {% endfor %}
</html>
```

---

{{< figure src="django-template-for2.png" >}}

Why not use an HTML ordered list?

---

```html
<html>
  <body>
  <h1>Hello {{ name }}!</h1>
  <h2> Topics include:</h2>
  <ol>
  {% for t in topics %}
    <li>{{ t }}</li>
  {% endfor %}
  </ol>
</html>
```

---

{{< figure src="django-template-for3.png" >}}

- Notice how we did not modify the view function!
- Which is great for designers!

---

## Template Tags

- The commands placed in {% %} blocks are called tags
- Try exploring:
  - [if, elif, and else](https://docs.djangoproject.com/en/3.2/ref/templates/builtins/#if)
  - [block and extends](https://docs.djangoproject.com/en/3.2/ref/templates/language/#template-inheritance)
- See the [template tags documentation](https://docs.djangoproject.com/en/3.2/ref/templates/builtins/#built-in-tag-reference)

---

## Filters

- Functions to control variable output in templates
- Programmers should not worry about how the data will be presented
  - It should be the designers job!

---

## Filter Example

Let's switch the name to lower case in our example:

```html
<h1>Hello {{ name|lower }}!</h1>
```

- Notice we added the pipe character | then the filter lower
- No space should be included between the variable, the pipe |, and the filter

---

## Other Template Filters

- Explore the [template filter reference](https://docs.djangoproject.com/en/3.2/ref/templates/builtins/#built-in-filter-reference)
- Find other useful filter you can use and apply them to the example
- Where would you think filters would be most useful?

