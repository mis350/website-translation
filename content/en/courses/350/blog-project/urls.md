---
# Page title
title: URLs

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: URLs

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 7

draft: false


---


## URL Paths

A well designed URL path will be readable, short, and easy to remember. It is the part from the url that determines which view Django will run and send to the browser. The paths can be static, where the path never changes. For example:


```
/blog/posts
/poll/list
/product/list
```

The paths can also be dynamic, where certain parts of the path can vary. For example:

```
/blog/post/10
/blog/post/234
/profile/khaled
/profile/ahmed
```

Notice the numbers in `/blog/post/10` and `/blog/post/234`. It's the number part is changing, but the pattern is generally the same `/blog/post/{number}` where the `{number}` part keeps changing. Similarly with `/profile/khaled` and `/profile/ahmed`, it is just the name part of the path that changes but both paths patterns are the same which is `/profile/{name}`.

These dynamic url paths are known as url patterns. They serve a specific purpose in web applications in that it allows the client to specify a value that the server can use to serve a specific item. You can view it as a way in which the server can accept input from the client. In our previous examples, the `/blog/post/{number}` url pattern means that the client will provide the `{number}` to the server through the url. Similarly with `/profile/{name}`, the client provides the name to the server using the url pattern.

While static url paths can allows us to create pages that list information, dynamic url patterns allows us to create pages where we can specify which item to display from the data. Typically, the dynamic part will hold the primary key in which the item to be displayed is chosen by.


## Defining URL Paths

The main file in which the url patterns are defined in is known as the root urls.py file. It can be found on replit Django projects in `mysite/urls.py`. Here are the paths defined in the web application will be found. To add a new path, simply add the pattern to the list of urlpatterns using the `path` funciton as shown in this example:

```python
urlpatterns = [ 
    path('test/', test_view),   
    path('blog/posts', blog_posts),   
]
```
To create a url path:
1. Add the path function to the list of urlpatterns in mysite/urls.py
2. Define the path as a string in the first parameter of the path function.
3. Import the view function you want linked to the path and pass it as the second argument in the `path` function.

In the above example, two paths were create. The first, links the path `test/` to the view function `test_view`. The second links the path `blog/posts` to the view function blog_posts. This means that if a browser should request the path `/test/` Django will run the function `test_view` and give the browser the HttpResponse returned from that function to the browser.


## Defining Dynamic Paths

Defining dynamic path is similar to static path. The only change is in how we write the path part that we pass to the `path` function. With static paths, we provide a static string (e.g., `test/`). However, with dynamic paths, we need to show which part of the path is the changing part of the pattern. For that, we include the symbol `<type:name>` in our string which tells django the type of data to expect, and the name to give that data. For example:

```python
path('profile/<str:name>/', user_profile),
path('blog/post/<slug:slug>/', view_post_by_slug),
path('blog/post/<int:id>/', view_post_by_id),
path('blog/post/<int:year>/<int:month>/', view_posts_in_month),
```

The first pattern patches `profile/<str:name>/` to the view function `user_profile`. Notice the `<str:name>` part of the pattern. This means that this part of the path is a changing string, therefore, Django will understand that it will run the function `user_profile` if it receives any of the following paths:

```
/profile/mohammad
/profile/ahmed
/profile/sara
/profile/khaled
...etc
```
The list is endless, because the `<str:name>` pattern allows for this. But because it is changing, we must also make a small change to the view function. Notice the `name` part in the pattern, this tells Django that the name part of the pattern must be passed to the view function as the variable name. Therefore, when defining the view function `user_profile` it must have an argument named `name` after the `request` argument. If not, Django will give an error that there is no way to deliver the name part from the path to the view function. So the `user_profile` function would look like this:

```python
def user_profile(request, name):
```

The argument name will contain the name part. So for the path `/profile/mohammad` the name argument will contain the string `mohammad`. For `/profile/ahmed` it will be `ahmed` and so on. 

The number of patterns in a path is not limited to a single one. We can also include multiple patterns. For example:

```python
path('blog/post/<int:year>/<int:month>/', view_posts_in_month),
```

However, the matching view function must also add an equivalent number of arguments that match the names of the patterns. So `view_posts_in_month` is defined as such:

```python
def view_posts_in_month(request, year, month):
```

## Improved URL Organization

Now imagine if we had hundreds of paths to define for our application. The root urls.py file will become a mess. So a better approach is to split it into multiple files and use the root urls.py to point Django to where to find these files. The Django admin is using this method. If you look at the `admin/` path in the root urls.py:

```python
path('admin/', admin.site.urls), 
```

Here, Django will fetch the urlpatterns defined in the admin app found in `admin/site/urls.py`. This is not a view function, but a collection of paths defined for the admin app. So all urlpattern will be found there and only a single entry is added to the root path. We can do the same for our `blog` app, where we create a urls.py inside the blog app to hole all the urlpatterns for the blog app, and point to it using a single entry in the root urls.py. 

So to organize to organize our paths for the blog app we must:
1. Create the file `urls.py` in our `blog` app directory
2. Include the paths for our applications in the `blog/urls.py` file
3. Point to the `blog/urls.py` in the root `urls.py` for any path that starts with `blog/`

Let's take a look at our current not very well organized root urls.py file, it looks like this:

```python
from django.contrib import admin
from django.urls import path
from blog.views import test_view

urlpatterns = [
    path('admin/', admin.site.urls),
    path('test/', test_view),   
]
```

What we want to do is move the path from our blog application `path('test/', test_view)` to the new `blog/urls.py`. All future paths we create for our blog app will also be created in `blog/urls.py` instead of `mysite/urls.py`. So Let's create first the `urls.py` file under the `blog` app directory, it should look like this:

```python
from .views import test_view #1
from django.urls import path #2

urlpatterns = [ #3
  path('test/', test_view), #4
]
```

Code explanation:
- Line 1: Notice the import uses relative importing because `urls.py` is not in the same `blog` directory as `views.py`. We imported here the `test_view` function we used in our previous examples. Another way to perform the import here would be to import the view module as such `from . import views`. This would allow us to refer to all view functions in the views.py module but every function must be preceded with `views.`. So `test_view` must be used as `views.test_view` if we use this alternative method of importing.
- Line 2: We must import the path function used to link view functions to path because we will use it here.
- Line 3: All paths must be included in the urlpatterns list, this is how Django finds them. We will add our patterns here as we continue this example.
- Line 4: This is the path we moved from the root `urls.py` to match the path `test/` to the function `test_view`

While we have created urls.py Django doesn't know where it is or that it will be used for paths. To complete our work we must link our new `blog/urls.py` to the root `urls.py`. So open the root `mysite/urls.py` and update it to look like this:

```python
from django.contrib import admin
from django.urls import path, include #1

urlpatterns = [
    path('admin/', admin.site.urls),   
    path('blog/', include('blog.urls')), #2
]
```
Code explanation:
- Line 1: We had to import a new function called `include` that we will use to include the paths from `blog/urls.py`. Notice also how we no longer import our `test_view` here because we don't need it.
- Line 2: here we are telling Django that any path that starts with `blog/` would be matched to the patterns found in `blog/urls.py`. This means that all the paths for our blog app **must** start with `blog/`. So our `test/` pattern defined in `blog/urls.py` will match to the path `blog/test/` but will not match to the path `test/`.

Let's now take advantage of urls patterns and do something more interesting with our blog app. Add the pattern `path('greet/<str:name>', greet_view),` to `blog/urls.py`, so it the file will look like this:

```python
from .views import test_view, greet_view #1
from django.urls import path

urlpatterns = [
  path('test/', test_view), 
  path('greet/<str:name>', greet_view), #2
]
```

Code explanation:
- Line 1: We imported thew new view function that we will create called `greet_view`
- Line 2: We linked greet_view to the path `blog/greet/<str:name>` where the `<str:name>` part will be a string passed through the argument `name` to the view function `greet_view`

Let's update our `blog/views.py` and add to it `greet_view`:

```python
def greet_view(request, name): #1
  data = {} #2
  data["name"] = name #3
  return render(request, 'greet.html', context=data) #4
```

Code explanation:
- Line 1: Notice we have included the argument name, because in `blog/urls.py` we matched `greet_view` to that pattern that contains `<str:name>`. So Django will pass the name string in the path to the argument `name`. therefore, we must include it after the request argument otherwise Django will throw an exception.
- Line 2: line 2, we are creating a context variable because we will be using templates.
- Line 3: We have included the name passed from the url path into the slot `name` in our context vairable. This means that the template will also have a variable named `name` that will contain the name part from the url path.
- Line 4: We are using render to generate an HttpResponse that include the greet.html file and use the context dictionary data to populate it with our data.

The last part of this new view is to create the template `templates/greet.html` which looks like this:

```html
<html>
  <body>
  <h1>Hello {{ name }}!</h1>
</html>
```

Notice how it includes the template variable name which we passed from our context variable. Now run the application and test it using the following paths:
```
/blog/greet/mohammad
/blog/greet/ahmed
/blog/greet/sara
```
Notice how every time you change the name part, the output of our view changes to display the name of the person mentioned in the path. This is one of many ways in which input is accepted from the user. But here it is limited to simple and specific type of input.

Now we have the bases in which to continue our blog application and create views to display database content from our app. We will use what we learned here to create a static url to display the list of available posts. Then, to display the details of a post, we will use a dynamic url pattern to specify a post slug in the path. We will go into the details of implementing this update in the next section.

## Final Thoughts

- Please read the [URL dispatcher documentation](https://docs.djangoproject.com/en/3.2/topics/http/urls/) for more information.
- An excellent explanation is provided in the [django documentation](https://docs.djangoproject.com/en/3.2/intro/tutorial03/#removing-hardcoded-urls-in-templates)

## Review Questions and Challenges
- Create a view to convert `pounds` to `kilos` where the path is `ptok/{weight_in_pounds}`, where `{weight_in_pounds}` is a number that is the weight in pounds, as an integer, that we want to convert to kilos. The view must display the message `xxx pounds is yyy kilos`. So you must perform the conversion in the view function. To convert pounds to kilos just multiply the weight in pounds by 0.454.
- Create another view that converts `kilos` to pounds this time and give it a different path. Convert kilos to pounds by multiplying the weight by 2.2.
- What are the steps to including the paths in the urls.py in the app directory instead of the root urls.py?
- what are the benefits of including the paths in the app urls.py instead of the root urls.py?
- What are the different data types you can define in a dynamic url pattern (you must read django documentation for this one)?
- How many dynamic patterns can you have in a single path?
- What's the difference between importing view functions as `from .views import view_function` or importing them as `from . import views`?


