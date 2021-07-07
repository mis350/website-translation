---
# Page title
title: ISOM 350 - Business Application Development

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Improved Admin

# Page summary for search engines.
summary: Second programming course for MIS majors utilizing Python to build data-driven business applications.

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 4

draft: False


---

{{% callout note %}}
Switch to branch **4-improved admin** from **malmarz/isom350-blog** github repo to see this step's implementation
{{% /callout %}}

In the previous step, we created a very simple default admin page. Django allows us to configure how the admin works by defining an ModelAdmin class in blog/admin.py.

We started with the following:

```python
from django.contrib import admin

from .models import Post

admin.site.register(Post)
```

Let's modify it to have a configurable admin interface by creating a PostAdmin class that inherits from the ModelAdmin class:

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
  pass

admin.site.register(Post, PostAdmin) # Notice this line changed
```

We can also register the PostAdmin like so:

```python
from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
  pass

```

See the `@admin.register(Post)` line. It tells Django that this admin class is for the Post models and registers it at the same time. You can use either methods to register a model admin and configure it.

Notice how we defined `class PostAdmin(admin.ModelAdmin)` which is empty. This means that inherits everything the ModelAdmin has to offer. If you test it you will notice nothing changed about our admin interface and that what we just did is just a longer version of what we did earlier. However, the new version is more flexible and allows as to configure the admin.

Once you register the Post admin, login to the admin interface and select the Post admin. You will be presented with the following screen:

{{< figure src="courses/350/djadmin/djadmin-list1.png" caption="Simple Post Model List" width=80%  >}}


**Note:** Your Post list will first be empty, once you create blog posts, then you will see them listed as in the figure.

Our figure shows two blog posts without much detail to them. Let's slightly improve the list by replacing the `post object` title in our list with a meaningful message. To do that, you must override the `__str__` model for the Post model. Open models.py and update the Post model:

```python
class Post(models.Model):
    # no change to attributes
    # title = models.CharField(max_length=200, unique=True)
    # .. etc

    # add the following method
    def __str__(self):
        return self.title
```

Once the `__str__` method is added to the post, the `post object` will be replaced with the title of the blog:

{{< figure src="courses/350/djadmin/djadmin-list2.png" caption="Improved Post Title Model List" width=80% >}}

Now let's try to take advantage of Django Model admin options to further improve the Post list to include other columns containing information about the each Post. Modify the code in admin.py to look like this:

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on') # This line was added

admin.site.register(Post, PostAdmin)
```

Here we requested that the table displaying the Posts should display a column showing the title, slug, status, and created_on fields. Our list of Post in admin now look like this:

{{< figure src="courses/350/admin-list.png" caption="Improved Admin Post List" width=80%  >}}

Next let's add the ability yo filter this list by status:

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added


admin.site.register(Post, PostAdmin)
```

Now we have the option to list all posts, the draft posts only, or published posts only:

{{< figure src="courses/350/list-filter.png" caption="Admin Post Filter" width=50% >}}

As you can see, whenever we want to configure the admin, we add an attribute (a line) that configures the features of the ModelAdmin for our posts and these configurations are reflected on our model admin.

Let's look at two more configurations, first, lets add the ability to search posts. Here we are adding the ability to search posts in the admin interface using their title and content fields:


```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added
    search_fields = ['title', 'content']

admin.site.register(Post, PostAdmin)
```

{{< figure src="courses/350/djadmin/djadmin-list-search.png" caption="Improved Admin Post List with Search" width=80%  >}}

Finally, when creating a post, we would like to pre-populate the slug field with information from the title. A slug is usually constructed by replacing spaces in the title with hyphens (-). Since this is a very common operation in web development, django provides it out of the box for us:

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added
    search_fields = ['title', 'content']
    prepopulated_fields = {'slug': ('title',)}
admin.site.register(Post, PostAdmin)
```

There is certainly much more about the Admin interface that we cannot cover in this course. The way to learn what is available is to keep reading the [Django admin documentation](https://docs.djangoproject.com/en/3.1/ref/contrib/admin/) and experimenting with new features.


