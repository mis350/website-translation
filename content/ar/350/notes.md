---
# Page title
title: my hidden notes

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: ISOM 350


# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 1

draft: true

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


## Study Plan

| Week  | Module | Topic  | Reading  | Project | Assignment | Slides
|---|---|---|---|---|---|---|
|  1 | Language Review | <ul><li>Python Data structures</li><li>Object Oriented Programming</li><li>Markdown</li></ul>|   |   |   |
|  2 | Project Management and Collaboration | <ul><li>Replit</li><li>Github Source Code Management</li><li>Github Issues</li><li>Github Boards</li></ul>|   |   |   |   |
|  3 | CRUD Applications</br>(Create/Read/Update/Delete operations) | <ul><li>Web App Develop</li><li>Django overview</li></ul> |   |   |   |   |
|  4 | Data Schema and Storage |  <ul><li>ER-Diagrams</li><li>Django Models and Fields</li><li>Django Admin</li></ul>  | Multiple projects | 3 projects, one in class, one in lab, one for assignments  |   |   |
|  5 | Showing a Single Objects (Read) | <ul><li>Fetching Objects</li><li>Django Views</li><li>Django Templates</li><li>URLs</li></ul>| using the same projects  |   |   |   |
|  6 | Listing Objects (Read) | <ul><li>Django Query Sets</li><li>Fetching a List of Objects</li><li>User Input from URL</li><li>Filtering Objects</li></ul>|     |   |   |   |
|  7 | Working With Relationships (Read) | <ul><li>One-to-One Relationship</li><li>One-to-Many Relationship</li><li>Many-to-Many Relationship</li></ul>|     |   |   |   |
|  8 | Deleting Objects (Delete) | <ul><li>Deleting an Objects</li><li>Deleting a List of Objects</li><li>Deleting Related Objects</li></ul>|     |   |   |   |
|  9 | Creating Objects (Create) | <ul><li>Creating an Object</li><li>Creating related Objects</li><li>User Input Using Forms</li><li>Django ModelForms</li></ul>|     |   |   |   |
|  10 | Updating Objects (Create) | <ul><li>Updating an Object</li><li>Updating a List of Objects</li><li>Using Forms to Update Objects</li></ul>|     |   |   |   |

Not sure how to cover all of this (organization I mean)
- Project based that get more complex?
- Or topic based?
- I think project based is better as it gives them opportunit to:
  - work before class to perform some tasks
  - After class to fix issues and work on next task
  - repeat practice and be reminded of big picture every time
  - we can get them to work together and collaborate
- Suggested projects:
  - MUST HAVE AN OVERVIEW OF STEPS TO WORK ON TO IMPLEMENT FEATURES
    - SOMETHING FOR WHEN A PROJECT STARTS
    - SOMETHING FOR ONGOING PROJECT
    - DETAIL COLLABORATION STEPS
    - Consider challengeing them with things to do as bonus
    - Need to create these projects myself
    - Lab will be to do a project with them? or help solve their problems? or solve the assignments I ask them?
  - Blog (no login, admin to enter data, then show posts, very simple)
  - Poll (now there is user input, still simple, no need for authentication, still main input from admin)
  - Chat (simple, but will need authentication now and use management)
  - Quiz (slitlight more complex poll, with user management or not, and with answers to calculate score, maybe expand to include question bank?)
  - ~~URL shortner (this is part of an app, not like bitly, but to shorten slugs ... I dont know .. maybe?)~~
  - A wiki showing history and all editors
  - Grading system? can add analytics dashboard, can be with authentication and without (this can be simple or complex, think more about it)
  - Recipies with search (social media website for recipies, create recipies, like and dislike, review (maybe reuse the chat app? or no chat?), and authentication)
  - Reservation system (seats? tables? time? calendar maybe to find conflicts? timeslot?)
  - Improved blog with search capability? maybe with time?
  - Kuwait News aggregator? (this needs backrunning process, might not be appropriate, or maybe a management task to pull news from a newspaper website? creating management tasks? prepopulate data)
  - e-commerce website .. not sure for final or we do it together?

NOTEs: 
- ModelForms vs formfactories ... maybe factories?
- List comprehensions will be introduced when needed ... next time should be part of python 230
- Readings will point to relevant Django Documentation, But I will create exercise and slides for class
- Do we use a project that we go through in class? then provide another project as a final? or get them to choose their project?
  - I think it is best if I prepare a project for them to use for the final if they do not come up with a good idea
  - Need to also to set parameters on what the project needs to be like based on the proposed project
  - Also need to think of multiple projects that we go through in class? maybe e-commerce (final project), blog, poll, dashboard for data analysis?, a search application? maybe recipies?, to-do application, reservation system, quiz application, image storage like instagram?, grading system, registration system (can be final as well), URL shortner, Kuwait News Aggregator 
- Consider including summary of the workflow for building a web application and tying it to the todo list, the ERD and how work is generally done .. display the workflow at the beginning .. in the middle .. and at the end
- Seems like using git and github could work if we use it with replit
- remember to set the run command for django on replit
- Crispy forms should be a bonus: https://medium.com/wdstack/django-crispy-forms-what-are-they-about-5bfa1ffa5187
- consider also giving homeworks where students would add a features .. or I suggest a feature that they search for and add
- 
### interesting links

- https://replit.com/talk/learn/A-Comprehensive-Guide-to-Replits-New-Git-and-GitHub-Features/23872
- https://github.com/git-tips/tips
- https://github.com/tiimgreen/github-cheat-sheet
- Using tickets on github effectively: https://guides.github.com/features/issues/
- projects are great!!! https://docs.github.com/en/github/managing-your-work-on-github/about-project-boards
- OOP VIDEOS: https://www.youtube.com/playlist?list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc

### Criteria for assessing projects
- Using GitHub for coordination properly
- Properly dividing work
- Using ticketing system effectively
- Having useful commit messages
- Taking advantage of new features
- minimum number of models, forms, and view functions


## useful tutorials

- https://pymbook.readthedocs.io/en/latest/
- https://www.learnpython.org/
- https://thepythonguru.com/
- https://pythonbasics.org/


## ToDo
- [ ] Assignment on Models (must refer students to documentation)
- [ ] Assignment on creating single objects
- [ ] assignment on querysets
- [ ] assignment on updating a single object
- [ ] assignment on updating multiple objects
- [ ] Maybe talk to them about the django shell?
- [ ] add textbook details, and include link
