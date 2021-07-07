---
title: Data-Driven Views
summary: Explore how we can leverage what we have learned so far by taking advantage of models, views, and templates to create some data driven views.
authors: []
tags: [isom350]
categories: []
date: "2021-05-12T12:07:04Z"
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

Data-Driven Views

---

### Quick Summary of Steps to Building a View

1. Create the view function in views.py
2. Link the view function to a url path in urls.py
3. Prepare the template for the page

It is the same for data driven-views, we just use Django models to fetch/store data in our view function

---

## Data-Driven Views

- Take advantage of Django Models and ORM to:
  - Store data
  - Update data
  - Fetch data
  - Delete Data
- Basically your CRUD operations

---

## Fetching Data

- Single object
- List of Objects

---

## Fetching Single Objects

- Model.objects.get is used (replace Model with your model)
- Using primary key or key (unique values)
- One object or none is returned

---

## Listing Blog Posts

Let's create the view function:

```python
from django.shortcuts import render
from .models import Post


def list_posts(request):
  posts = Post.objects.all()
  context = {
    'post_list': posts,
  }
  return render(request, "post_list.html", context)

```

---

## Let's Link the View to a URL Path

We are now Django experts, so we link the urls.py in our app to the room urls.py:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),   
    path('blog/', include('blog.urls')), # includes paths from blog/urls.py
]
```

---

## Defining The Path

Now we can define all our paths in blog/urls.py:

```python
from . import views 
# Alternatively:
# from .views import list_posts
from django.urls import path

urlpatterns = [
    path('', views.list_posts),
]
```

---

## Adding The Last Missing Part

- Make sure the directory blog/templates is created
- Create post_list.html inside it

  
---

## post_list.html

```html
<!doctype html>
<html lang="en">
  <head><title>Post List</title></head>
  <body>
    <h1>Latest posts:</h1>
    <ul>
      {% for post in post_list %}
      <li>{{ post.title }}, posted on {{ post.created_on }}</li>
      {% endfor %}
    </ul>
  </body>
</html>
```


---

## The Result

{{< figure src="django-ddv-result.png" >}}

---

## Database Queries

Remember this line from views.list_posts:

```python
posts = Post.objects.all()
```

Here we are using the Django ORM to fetch all blog posts

---

## Details of Database Queries

```python
posts = Post.objects.all()
```
- posts: is the variable that will store the results (a list)
- Post: is the model we are querying, since we want posts
- objects: is known as a model manager, it has all the database related functions
- all: is our query

---

## Improved Query

- Instead of all, let's use the filter command to fetch published posts only:

```python
posts = Post.objects.filter(status=1)
```

- status: is the field we want to query on, from models.py (see definition of Post model)
  
---

## Improved Query

```python
posts = Post.objects.filter(status=1)
```

- Notice we use =, not ==, this is very important
- status=1: means we want all Posts in which status is equal to 1
  - Remember, 1 is published, and 0 is unpublished as defined in models.py
- Can you change query to list unpublished posts?
  

---

## Basic Query Syntax

- Use the filter method on the objects model manager
- Filtering syntax is:
```
field_name = value
```
- However, this is for exact value matching
- What if we want to perform non-exact matching or date searchers?

---

## You Must read the Documentation on Queries

1. [Making queries documentation](https://docs.djangoproject.com/en/3.2/topics/db/queries/)(Required Reading!)
2. [QuerySet reference](https://docs.djangoproject.com/en/3.2/ref/models/querysets/)(See what is available to use)
  - Suggested methods to read about:
    - exclude, order_by, reverse, count, latest, earliest, first, last, exists
    - aggregate and annotate might seem confusing at this time, we will cover them later
  
---

## Improved Query Syntax

- Using the double underscore __, you can use special lookup function
- Improved filtering syntax using lookups:
```
field_name__lookup_function = value
```
- Read the [documentation for lookup functions](https://docs.djangoproject.com/en/3.2/ref/models/querysets/#field-lookups)

---

## Lookup Query Example

To fetch all posts with the word 'first' in the title:

- Using case sensitive search:
```python
Post.objects.filter(title__contains='first')
```

- Using case insensitive search:
```python
Post.objects.filter(title__icontains='first')
```

---

## Lookup Query Example

- You can use the following lookups exactly like contains and icontaint:
  - startswith, istartswith, endswith, iendswith, exact, and iexact
- Can you modify to search the body instead?
- What's the difference between exact and contains?

---

## Empty Field Lookup

- Typically isnull is used
- Find empty fields (not modified):
```python
Post.objects.filter(updated_on__isnull=True)
```
- Find non-empty fields (modified):
```python
Post.objects.filter(updated_on__isnull=False)
```

---

## Searching For Empty Strings

- If the CharField of TextField is defined with null=True
  - Then use the lookup isnull=True
- It is possible that someone would store an empty string
  - To find those use the lookup field=""
- Be aware that null and empty string "" are very different

---

## Numeric Value Lookups

- When looking up numeric values we perform comparisons:
  - gt: Greater than
  - gte: Greater than or equals
  - lt: Less than
  - lte: Less than or equals
- What about equals?

---

## Date/Time Lookups

- The typical date/time lookup methods can be classified into either:
  - Exact date/time lookup
  - Range lookup

---

## Exact Date/Time Lookups

- Using any combination of __year, __month, __day, __hour, __minute, and __second lookup to get a specific date
- For example...

---

### For posts created in the year 2020
```python
Post.objects.filter(create_on__year=2020)
```

---


### For posts in January 2020:
```python
Post.objects.filter(
  create_on__year=2020,
  create_on__month=1,
  )
```

---


### For posts in 23rd of January 2020:
```python
Post.objects.filter(
  create_on__year=2020,
  create_on__month=1,
  create_on__day=23,
  )
```

---

## Exact Date/Time Loockups

- How can you lookup posts created:
  - on the1st of every month?
  - at 2am (any date)
  - at 5pm on March 2nd (regardless of the year)
  - at 5pm on March 2nd in 2019 

---

## Range Lookup for Date/Time

- Ranged lookups can have 3 forms:
  1. Filter all dates BEFORE (Less than) a specific date/time 
  2. Filter all dates AFTER (Greater than) a specific date/time
  3. Filter all dates BETWEEN two dates/times

---

## Range Lookup for Date/Time

For all three cases you need to do the following:

1. Import datetime python library
2. The lookup dates/times must be either:
   - datetime.date object (for dates only)
   - datetime.datetime object (for date and time)
3. Use the date and datetime objects as the value to lookup
4. For datetime fields, use __date after field name to perform a date only lookup

---

## Filter Before a Date/Time Example

```python
import datetime
date_before = datetime.datetime(2019, 5, 3, 0, 0, 0)
posts = Post.objects.filter(created_on__lt=date_before)
```

- Can you tell the difference between using lt and lte here?
- What is the 0,0,0 part? (it's optional btw)
- What is the default time if we exclude it?

---

## Filter After a Date/Time Example

```python
import datetime
date_before = datetime.date(2019, 5, 3)
posts = Post.objects.filter(created_on__date__gt=date_before)
```

- Notice we are doing date comparison only here, see the __date after created_on
  - Django will ignore the time
- As with lt and lte, gt is exclusive, while gtw is inclusive of the query date.


---

## Check If Date/Time Has Passed


```python
import datetime
posts = Appointment.objects.filter(
  scheduled_on__lt=datetime.datetime.now()
  )
```
- Use `datetime.datetime.now()`  or `datetime.date.today()`
- If date/time is 
  - gt now/today, then it's in the future
  - lt now/today, then it's in the past
  

---

## Between Dates/Times Lookup

- Same rules apply as with before and after lookup
- Use __range instead of __lt or __gt 
- Passed value must be a tuple containing the range dates/times
- The range is inclusive (like __lte and __gte)

---

## Between Dates/Times Lookup Example

```python
import datetime
start_date = datetime.datetime(2019, 1, 3)
end_date = datetime.datetime(2019, 3, 25) # after start_date
posts = Post.objects.filter(
  created_on__range=(start_date, end_date)
  )
```

- Range is from midnight start of start_date to midnight start of end_date, so Posts during end_date are not included
- Mixing of date with datetime in range is not allowed
- Range can be used with numeric fields also

---

## Filtering and Searching The List

- To add a search or filter feature to the list the following is needed
  1. A urlpatterns that accepts a query
  2. A view function that uses the query to filter the list
  3. Everything else remains the same

---


## Search/Filter Updated blog/urls.py

1. A urlpatterns that accepts a query:
   
```python
from . import views 
from django.urls import path

urlpatterns = [
    path('', views.list_posts),
    path('search/body/<str:q>/', views.search_posts),
]
```
  - Notice how the path has meaning
---

## Search/Filter Updated blog/views.py
2. A view function that uses the query to filter the list, Just add the following view function:
```python
def search_posts(request, q):
  posts = Post.objects.filter(body__icontains=q)
  context = {
    'post_list': posts,
  }
  return render(request, "post_list.html", context)
```

---

## Compare search_posts to list_posts

```python
def list_posts(request):
  posts = Post.objects.all()
  context = {
    'post_list': posts,
  }
  return render(request, "post_list.html", context)
```
---

## The Search View is Complete

- Included q argument for the query to search view function
- Used filter to get posts that match query
  - Here we searched the body
- Reused the same template post_list.html
- That's it!
- Can you do a search/filter for titles? or created_on dates?

---

## Complex Lookups

- If you want to use complex lookup conditions
- For example, a query that matches the body OR the title
- Read the documentation on [Django Complex Queries](https://docs.djangoproject.com/en/3.2/topics/db/queries/#complex-lookups-with-q-objects)

---

### Other interesting Lookups to Investigate

- in
- week, week_day, and quarter (for Date/DateTime)
- regex and iregex
- See [Djangos QuerySet Lookup documentation](https://docs.djangoproject.com/en/3.2/ref/models/querysets/#field-lookups)

---

### Fetching Single Objects

- Just replace filter with get
- get must return a single object (not a list) otherwise it will through an Exception
  - For our Post models, the exception classes are:
    - Post.DoesNotExist if object was not found
    - Post.MultipleObjectsReturned if multiple objects return (not unique)
- Typically use for primary key lookup

---


### Updating Blog to Show Post Details

Let's create the view for displaying a Post:

```python
def show_post(request, id):
  post = Post.objects.get(slug=id)
  context = {
    'post': post,
  }
  return render(request, "post_detail.html", context)
```

- We will get the id from the URL path, so we include it as a view function argument.
- Can you use get_object_or_404 instead?
---

### Shortcut for Using Get

- Django provides the shortcut function `get_object_or_404` that doesn't through an error, but displays the 404 page instead
- 404 error means the page is not found
- Most common use case
```python
from django.shortcuts import get_object_or_404
from .models import Post

def show_post(request, pid):
  context = {
    post = get_object_or_404(Post, pk=pid)
  }
```

---

### Updating blog/urls.py

List of urlpatterns should look like this:

```python
  urlpatterns = [
    path('', views.list_posts),
    path('search/body/<str:q>/', views.search_posts),
    path('<slug:id>/', views.show_post),
  ]
```

For show_post, Django take whatever slug is in the url and pass it as the id argument to the show_post view function

---

### Adding the Template

Add post_detail.html to blog/templates, it should contain the following:

```html
<!doctype html>

<html lang="en">
<head><title>{{ post.title }}</title></head>
  <body>
    <h1>{{ post.title }}</h1>
    <p>{{ post.body }}</p>
    <pre>Posted on: {{ post.created_on }}</pre>
    <pre>Updated on: {{ post.updated_on }}</pre>
  </body>
</html>
```

---

### The Result

{{< figure src="django-ddv-result2.png" >}}

Make sure you open the path /blog/blog-post-slug and replace blog-post-slug with the correct slug value for the post you want to view

---

### Adding Links from Post List View

Update the template post_list.html, specifically this line:

```html
  <li>{{ post.title }}, posted on {{ post.created_on }}</li>
```

Replace it with this:

```html
  <li>
    <a href="/blog/{{ post.slug }}">
      {{ post.title }}, posted on {{ post.created_on }}
    </a>
  </li>
```
Change it to make the title only clickable

---

### Result

{{< figure src="django-ddv-result3.png" >}}

Now you don't have to remember post slugs as they are now clickable


