---
# Page title
title: ISOM 350 - Business Application Development

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: ISOM 350

# Page summary for search engines.
summary: Second programming course for MIS majors utilizing Python to build data-driven business applications.

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 1

draft: False

# Featured image
# To use, place an image named `featured.jpg/png` in your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
# Set `preview_only` to `true` to just use the image for thumbnails.
image:
  placement: 1
  caption: "Python logo"
  focal_point: "smart"
  preview_only: false
  alt_text: Python logo

---

## Requirements

We will mainly use the replit.com cloud IDE for development. To setup for this course, you will be required to perform the following:

- Read the [Syllabus](https://bit.ly/mis350_syl)
- Signup for [class replit team](https://replit.com/teams/join/slpharshbwpedtcbfdfsnrkqjlkjpabh-miscba)
- Signup for [{{< icon name="github" pack="fab" >}}github.com](https://github.com/join)
  - Complete the first [GitHub assignment to join our GitHub classroom](https://classroom.github.com/a/vOMY045D)
- Completion of an introductory course in programming (Doesn't have to be Python)

## Required References

- {{< icon name="book-open" pack="fas" >}} This website starting with [Introduction section]({{< ref "courses/350/intro" >}})
- [{{< icon name="file-powerpoint" pack="fas" >}}Slides for this course]({{< ref "courses/350/slides" >}})
- [{{< icon name="python" pack="fab" >}}Django's Documentation](https://docs.djangoproject.com/en/3.1/)


## Optional Requirements

- Textbook from Prerequisite course is a useful reference:


  Tony Gaddis, [Starting Out with Python](
https://www.pearson.com/uk/educators/higher-education-educators/program/Gaddis-Starting-Out-with-Python-Global-Edition-4th-Edition/PGM1963337.html), Global Edition, 4th Edition
  Haywood Community College, 2019 [{{< icon name="file-pdf" pack="fas" >}} Purchase Online](https://collegestudenttextbook.org/product/starting-out-with-python-global-4th-edition-ebook/)

{{< spoiler text="view other optional requirements.." >}}
While this is not required, should you choose to run a Django development server locally on your machine to avoid using the internet while development, you will need to install the following packages:

- Install [anacoda python](https://www.anaconda.com/products/individual#Downloads)
- Install [Visual Studio Code](https://code.visualstudio.com/download)
- Install Django using terminal on mac, or CMD on windows, by typing:
```bash
pip install django
```

**Note:** It will be your responsibility to read the Django documentation on how to setup the development environment on your computer.
{{< /spoiler >}}

## Study Plan


| Week  | Topic  | Slides | Assignment  |
|---|---|---|---|
| 1 | [Introduction]({{< ref "courses/350/intro" >}})  |  [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/intro" >}}) | [Complete course requirements]({{< ref "courses/350/#requirements">}})  |
| 2 |  [PyReview]({{< ref "courses/350/intro/python" >}})  | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/python" >}})  |  [Form Project Teams on GitHub](https://classroom.github.com/g/kxc1jQKA) |
| 3 |  [Collaboration]({{< ref "courses/350/intro/collab" >}})  | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/collab" >}})  | [Collboration Exercise](https://classroom.github.com/g/7iv9aOyv)  |
| 3 |  [Project Management]({{< ref "courses/350/intro/proj-mgt" >}}) | | [Help translate this website](https://github.com/mis350/website-translation) |
| 3 |  [Web Applications]({{< ref "courses/350/intro/webapplications" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/webapps" >}})  |  |
| 4 |  [Django Overview]({{< ref "courses/350/intro/dev-process.md" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/django-overview" >}}) | |
| 4 |  [Project Setup]({{< ref "courses/350/blog-project/setup.md" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/django-overview" >}}) | [Poll Project - Part 1]({{< ref "courses/350/poll-proj/part1.md" >}}) |
| 4 |  [Data Models]({{< ref "courses/350/blog-project/models.md" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/django-models" >}}) | |
| 5 |  [Django Admin]({{< ref "courses/350/blog-project/admin.md" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/django-admin" >}}) | |
| 5 |  [Improved Django Admin]({{< ref "courses/350/blog-project/improved-admin.md" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/django-admin" >}}) | |


