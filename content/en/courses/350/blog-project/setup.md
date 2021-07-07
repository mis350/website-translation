---
# Page title
title: Django Project and App Setup

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Setup

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 1

draft: False

---

{{% callout note %}}
Switch to branch **1-setup** from **malmarz/isom350-blog** github repo to see this step's implementation
{{% /callout %}}

To setup our blog project, create a replit using **Django Template**. You will initially get a code structure that looks like the following:

{{< figure src="courses/350/project-structure.png" caption="Project Structure" >}}

We must then create an app directory for our code because in Django, we must create at least a sinlge app in our project to be able to write code. We use the shell commands provided by Django to easily generate the app directory that will hold our code by first openning the shell:

{{< figure src="courses/350/shell.png" caption="Using the Shell" >}}

Now in the shell, type the following command:

```bash
python manage.py startapp blog
```

The system will perform a few tasks and you will notice that a new **blog** directory is created in your project containing a set of files:

{{< figure src="courses/350/app.png" caption="Blog App Directory" >}}

**If you do get an error** when typing the command click on the Run{{< icon name="play" pack="fas" >}} button up top and make sure everything is running correctly, then stop the server and type the startapp shell command again and it should work this time. If your project was setup correctly, you should see the following screen:

{{< figure src="courses/350/dev-server.png" caption="Django Development Server Running" >}}

The app directory will contain the standard files you will need to put your code in. They are:
1. **admin.py:** Using to configure the admin interface for managing all the data.
2. **models.py:** Where you put the data definitions for your blog application.
3. **views.py:** Where you put all the functions to handle HTTP requests and generate the HTTP responses.

These are the most important ones that you need to know at this time, and you will also need to create a few others as we progress in the project. 

Typically, we keep related features in their own app directoy. Every project must have at least a single app directory to hold the functionaloty created by the developer. If for example we need to include a shopping cart in our blog or an ecommerce component, we can create another app in our project named **cart** and place all ecommerce functionality in that directory. Similarly, we we introduce authentication and user management we would create an **accounts** directory and include all user management functionality there. So the apps are a matter of organization. 

The general rule is to organize related functionality in the same directory. Developers will differ in how they organize functionality and how related they see things are. With experience, you will improve in organizing your project. At this stage of your career, how you organize your code will not have a significant impact on your project. It is mostly related to the reusability of the app in other projects, which might be important to you in the future.

## Adding the App to Our Project

This step is necessary to let Django know that we want to use this app as part of our project.

Open `mysite/settings.py` then update the `INSTALLED_APPS` list to include our new blog app:

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',  # Make sure this line is added
]
```
