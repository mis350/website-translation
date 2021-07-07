---
title: Django Admin
summary: Configuring the django Admin for Your Project
authors: []
tags: [isom350]
categories: []
date: "2021-04-27T14:42:08Z"
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

Django Admin

---

## What is the Django Admin

- Web interface that allows the web application developer/admin to manage data
- Provides simple CRUD functionality to all defined models
- Must be configured by the web developer to be enabled

---
 ## Configuring the Django Admin

 1. Models must be defined in your app
 2. Configure database and perform migrations
 3. Create a superuser
 4. Register model to be managed by admin in admin.py
 5. Optionally configure the admin for the model in admin.py

---

## Creating a super user

Run the following management command in shell then follow instructions:

```bash
python manage.py createsuperuser
```

---

## Registering a Model with Admin.py

1. Import the model
2. Pass it to admin.site.register
3. Repeat for every model you want to manage in admin
   
```python
from django.contrib import admin

from .models import Post

admin.site.register(Post)
```

---

## Configuring the Admin

- Admin interface is more useful if properly configured
- Configuration will require defining a configuration class in admin.py
- Class provides information to Django on:
  - How a list of objects will be displayed
  - How single object can be created/viewed

---

## Creating an Empty Admin Configuration Class

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
  pass

admin.site.register(Post, PostAdmin) 
```

---

## Alternative Method

```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
  pass

```

---

## Result

{{< figure src="courses/350/djadmin/djadmin-list1.png" caption="Simple Post Model List" width=80%  >}}

---

## Improve Display Label for Post

```python
class Post(models.Model):
  STATUS = (
    (0,"Draft"),
    (1,"Publish")
  )

  title = models.CharField(max_length=200, unique=True)
  slug = models.SlugField(max_length=200, unique=True)
  body = models.TextField()
  created_on = models.DateTimeField(auto_now_add=True)
  updated_on = models.DateTimeField(auto_now=True)
  status = models.IntegerField(choices=STATUS, default=0)

  def __str__(self):
    return self.title
```

---

## Result

{{< figure src="courses/350/djadmin/djadmin-list2.png" caption="Improved Post Title Model List" width=80% >}}

---

## Configuring Displayed Columns

```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
  list_display = ('title', 'slug', 'status','created_on')

```

---

## Result

{{< figure src="courses/350/admin-list.png" caption="Improved Admin Post List" width=80%  >}}

---

## Filter Option

```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
  list_display = ('title', 'slug', 'status','created_on')
  list_filter = ("status",)
```

---

## Result

{{< figure src="courses/350/djadmin/djadmin-list-filter.png" caption="Admin Post Filter" width=80% >}}

---

## Adding search Option

```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
  list_display = ('title', 'slug', 'status','created_on')
  list_filter = ("status",)
  search_fields = ['title', 'content']
```

---

## Result


{{< figure src="courses/350/djadmin/djadmin-list-search.png" caption="Improved Admin Post List with Search" width=80%  >}}


---

## Adding Slug Prepopulation


```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
  list_display = ('title', 'slug', 'status','created_on')
  list_filter = ("status",)
  search_fields = ['title', 'content']
  prepopulated_fields = {'slug': ('title',)}
```

---

## What About Relationships?

```python
class Author(models.Model):
    first_name = models.CharField(max_length=50)
    last_name = models.CharField(max_length=50)
    country = models.CharField(max_length=100)

class Book(models.Model):
    author = models.ForeignKey(
      'Author', on_delete=models.CASCADE)
    title = models.CharField(max_length=100)
    release_date = models.DateField()
    num_stars = models.IntegerField()
```

---

## Use Inline Admins

```python
from .models import Author, Book

class BookInline(admin.TabularInline):
    model = Book

@admin.register(Author)
class AuthorAdmin(admin.ModelAdmin):
    inlines = [
        BookInline,
    ]
```
Why not register Book Admin?

---

## Result

{{< figure src="courses/350/djadmin/djadmin-inline-table.png" caption="Book Inlined as Table Within Author" width=80%  >}}

---

## Stacked Inline

```python
from .models import Author, Book

class BookInline(admin.StackedInline):
    model = Book

@admin.register(Author)
class AuthorAdmin(admin.ModelAdmin):
    inlines = [
        BookInline,
    ]
```

---

## Result

{{< figure src="courses/350/djadmin/djadmin-inline-table.png" caption="Book Inlined as Stack Within Author" width=80%  >}}

---

## Other Important Configurations to Investigate

- exclude, fields
- list_display, list_display_links
- readonly_fields, search_fields
- max_num, min_num (InlineModelAdmin only)
- Admin Actions (Advanced)

---

## Admin Reference

- For more information on configuring the admin interface, [please read the django documentation](https://docs.djangoproject.com/en/3.2/ref/contrib/admin/)