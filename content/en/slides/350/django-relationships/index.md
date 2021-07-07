---
title: Traversing Relationships
summary: How we can traverse relationships in django objects and fetch/present them appropriately in views/templates
authors: []
tags: [isom350]
categories: []
date: "2021-05-24T05:06:22Z"
draft: false
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

Traversing Relationship

---

### Relationship in Django

- Represented in models using
  - ForeignKey
  - OneToOneField
  - ManyToMany Field

---

### Updating our Blog App

- Each blog post will have multiple comments
- Comment author will provide comment, optional name, and optional email
- Comments will be displayed along with author name in order below the post
- Date/Time of comment will be displayed next to it
- Number of comments and date/time of latest comment will be shown next to each post in post list

---

### Updated ERD

```mermaid
erDiagram
    POST ||--o{ COMMENT : Has

    POST {
        string title
        string slug
        string body
        datetime created_on
        datetime updated_on
        int status 
    }

    COMMENT{
        string comment
        string author
        string email
        datetime created_on
    }
    
```
---

### Updated Models.py

```python
class Comment(models.Model):
  comment = models.TextField()
  author = models.CharField(max_length=100, blank=True, null=True)
  email = models.EmailField(blank=True, null=True)
  created_on = models.DateTimeField(auto_now_add=True)
  post = models.ForeignKey('Post', on_delete=models.CASCADE) 
```

---

### Admin and Migrations

- Create an inline Admin for the Post
- Don't forget makemigrations and migrate, why?
- Create at least 2 posts
- Create 2 comments for 1st post, and 3 comments for 2nd post.

---

### Traversing Relationship

- How do we display comments for each post?

---

## From Comment to Post

- The Many to One direction
- Just reference the relationship field:

```python
comment = Comment.objects.get(pk=id)
post = comment.post
```
- The post field will give you a Post object

---

### From Post to Comment

- The One to Many direction
- Use reverse relationships
- For every relationship Django makes available a field in the related model to allow moving in the other direction

--- 

### From Post to Comment

- For ForeignKey the reverse relationship gets the name model_set, for example comment_set in the current example
- It's just a model manager like objects, you can use all() and filter() on it
- Everything you learned about fetching objects using all and filter applies here as well
  
---

```python
post = Post.objects.get(pk=pid)
comments = post.comment_set.all()
```
- comments will include only the comments that belong to the post object in this example
- comments will be a list of objects
  
---

### The Reverse Relation Model Manager

- Everything you learned about the objects model manager applies
  - You can use all, filter, and get
  - also update, create, and delete (yet to be covered)
  - Applies to ForeignKeyField, ManyToManyField, and OneToOneField, but slightly different
  - Read the [documentation on model fields](https://docs.djangoproject.com/en/3.2/ref/models/fields/)

---

### Modifying The Reverse Relationship Name

- The attribute name by default is modelname_set
- Can be changed using the related_name option in Comment mode in models.py
```python
  post = models.ForeignKey('Post', 
    on_delete=models.CASCADE, 
    related_name="comments") 
```  
- Will replace `post.comment_set` with `post.comments`
- Useful for ManyToMany or multiple relationships of the same type
---

### Remember

- When traversing relationships, you are just fetching related data.
- Everything else about the view is just the same

---

### Updated Blog views.py

```python
def detailed_post_view(request, slug):
  data = {}
  post = Post.objects.get(slug=slug)
  data["post"] = post
  data["comments"] = post.comment_set.all()
  return render(request, "detailed_post.html", context=data)
```
- What if you wanted to filter comments to exclude ones without a name?

---

### detailed_post.html Template

```html
 <h1>{{ post.title}}</h1>
  <ul>
    <li>Posted on: {{ post.created_on }} </li>
    <li>Last updated: {{ post.updated_on }} </li>
  </ul>
  <p>
    {{ post.body }}
  </p>
  <h2>comments:</h2>
  <ul>
  {% for c in comments %}
    <li>{{ c.author }}: {{ c.comment }}</li>
  {% endfor %}
  </ul>
```

---

### The Result


{{< figure src="django-relationships.png" >}}

Do not forget to wire the urls