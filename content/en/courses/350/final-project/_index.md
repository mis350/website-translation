---
# Page title
title: Final Project

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Final Project

# Date page published
date: 2021-06-08T18:54:13Z

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 1

draft: False
---

{{% callout note %}}
Demonstrations are due on last day of our class, June 30th during class time
{{% /callout %}}

## Requirements

- [Signup your team](https://classroom.github.com/g/spcUH6KJ) and write the requirements and ER-Diagram in the Readme file of the repository.
- Convert the requirements to tickets by creating a project in the GitHub repository of your project and choose an appropriate name for your project:

{{< figure src="github-project.jpg" >}}

- Project requirements must satisfy the following:
  - [ ] Has at least 6 data models, with at least 2 relationships
  - [ ] Has at least 3 views to list data one of which is a search or filter functionality
  - [ ] Has at least 3 views to view specific data objects in the web app
  - [ ] Has least 4 views that allow user to create or update new data with one of the views that displays data containing a creation form
  - [ ] There is at least a single view that calculates statistical data and aggregations about the project

**Important Note**: While the main operations in a data-driven web application are Creat, Read, Update, and Delete, in an actual application, the view might not be name create or update. Instead, it might be called **purchase product**. This is a data creation view because product data is inserted in a cart database table. Similarly for paying, it involves creating and updating data.

## Grading The Final Project

### 1. The Demonstration (30%)

  Each team will be given 10 minutes to demonstrate their web application and show that it works. In the ten minutes you need to perform the following:
  1. Introduce the team members and the general idea of the web application
  2. Demonstrate the main operation in the app from your choosing and not necessarily all the features. But make sure you show the best parts of your application and show that it is well designed and works (Try to sell it to me or get me to invest in it).
  3. Be prepared for a Q&A session about the idea of the app (why you think it is valuable), using th app, and technical questions about the app.

  In the demo, you will mostly be evaluated based on:
  - How well you utilize your time
  - How well you present your web app and convince us of its value
  - How well the features you implemented meet the main requirements of the app
  - How well you have prepared the app (be sure to include test data and plan how you will show your app)
  - How well you answers questions (whether technical about the app/design or business about the idea)
  - How well your application works


### 2. The Collaboration (25%)

Teams are expected to utilize what they have learned in this course about GitHub and Collaboration. Evaluation will be based on:
- How well you get everyone involved in project development and management
    - Contributing to development
    - Contributing to project management
- How well you utilize GitHub for collaboration and project management, which include:
    - Properly using pull requests
    - Properly using tickets
    - Having clear communication and guidelines in the readme for the team to read


### 3. Individual Contribution (25%)

  Individual contribution will be based on:
  1. The amount of work done by the individual as reported by GitHub (focused on code)
  2. Peer evaluation

### 4. The Code (Including Bonus) (20%)

 A final review of the code by the instructor will be performed after the demonstration where the grade is determined based on:

 1. How well organized and clear the code is 
 2. Naming of paths, view functions, and models
 3. How appropriate are the model definitions
 4. How well the code meets the minimum requirements mentions in the requirements sections above (number of views ..etc)
 5. Include a list of bonus additions in the main Readme.md file. List any new features that you used that we haven't talked about in class. Be sure to list each bonus and in which file/line number the work is done. **Failure to follow this instruction would mean that the project team would not receive any bonus points, only listed bonus items will receive grades**.

### Code and Demo Evaluation

This is an example list of some of the issues I will look for when evaluating your project demo or code, whether:

- All 4 CRUD operations exist for all data models
- All views are linked to the main page of the app
- Confirmation is used in delete
- How deep the links are in your app
- Are all views created for all operations, or do you rely on Django admin, and what is your justification if using Django admin.
- Is there enough and useful data in the system when performing the demo
- How well does the django models reflect the ERD and whether ERD is appropriate given the requirements
