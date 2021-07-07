---
# Page title
title: View Functions

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Views

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 5

draft: True

---

{{% callout note %}}
Switch to branch **5-views** from **malmarz/isom350-blog** github repo to see this step's implementation
{{% /callout %}}


Views are functions that take the HTTP request from the webserver, process the request, then return an appropriate HTTP response. It is the function responsible for handling the main tasks of our web application and are also responsible for constructing the HTML page that will be returned to the client.

In our [brief introduction to Django]({{< ref "dev-process#4--create-view-function" >}}), we gave an overview of the simplest form of view function and what they need to do. Django also provides other means by which we can create view functions to perform standard tasks with very minimal coding.

One of the main functions in a CRUD based web application, such as the blog project we are working on, is its ability to display:

1. The details of a single item stored in our database
2. A listed (of filtered list) of items stored in our database.

In our case, the item in our database is the blog post. We want the means by which we can display the details of a single blog post and also a list of available blog posts. This is almost a universal requirement in all web applications. Django recognizes this and has made creating view functions for list and detailed object views very easy. It provides ready made views to perform standard functions called generic views. To use them, you take advantage of the OOP design of Django and extend the required view to your specific needs, exactly like what we did with the models and the improved admin interface.

Let's create a view to view a single post. To do that, we need to extend the [DetailedView generic view](https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-display/#detailview). We just specify the model we want to display its details and specify the template we want Django to use to present the data. This is how it is done in views.py:

```python
# First we import generic views
from django.views import generic
# We import also our Post model
from .models import Post

# Now we extend the DetailedView to create our fiew function
class PostDetailView(generic.DetailView):
  model = Post  # We want to display posts
  template_name = 'post_detail.html' # More about templates later

```

And we are done!. For the detailed view, the user of the website must specify a Post that they would like to view and Django will serve a page containing the details of that post. In web applications, the required post is specified in the path part of the url. We will later design our application to fetch a post either based on its ID or its Slug. So if the user requests `/post/1/`, Django would serve the details of the first post. Similarly for `/post/2/` or `/post/3/`. More on that when we cover URLs.

Let's prepare the view function for displaying the list of posts. For that, we extend the [ListView generic](https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-display/#listview) function in views.py as follows:

```python
# We create our view by extending ListView
class PostListView(generic.ListView):  
  # the "QuerySet" used to fetch the list of posts
  queryset = Post.objects.filter(status=1).order_by('-created_on')
  # more about templates later
  template_name = 'post_list.html'
```

The only difference between using ListView and DetailedView is that in DetailedView we specified a model, and the view will fetch a single object from that model type. With ListView, we specify a QuerySet. A QuerySet in Django is like a select statement in SQL, it is used to fetch a group or list of object that match a specific criteria. Here, the QuerySet to used to fetch Post objects, that have status = 1 (i.e., published posts), and they must be ordered newer first. Then the template tells Django how to show them.

QuerySets is one of the most important features of Django and complement Django database models. It allows us to control what data is fetched from the database. For more information on how to work with database objects and QuerySets, please refer to [Django's documentation on QuerySets](https://docs.djangoproject.com/en/3.1/topics/db/queries/).

Once you are done, the view.py file will look like this:
```python
from django.views import generic
from .models import Post

# Create your views here.
class PostListView(generic.ListView):
  queryset = Post.objects.filter(status=1).order_by('-created_on')
  template_name = 'post_list.html'

class PostDetailView(generic.DetailView):
  model = Post
  template_name = 'post_detail.html'
```

Now the view function is created, but it is not yet exposed to our users. They cannot access it from their browsers. For that, we must wire the view function to the website URL and assign it a path as we shall do in the next step. 

For more information on useing [Django's generic view please refer to Django's documentation](https://docs.djangoproject.com/en/3.1/topics/class-based-views/generic-display/).