---
# Page title
title: The Poll Project 2nd Assignment

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Part 2

# Date page published
date: 2021-05-26T16:24:05Z

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 40

draft: False

---

{{% callout note %}}
Due Date is <strong>Sunday June 6th before 1st lab</strong>
{{% /callout %}}

## Requirements for This Assignments (50 pts)

- [ ] **(5 pts)** Input some data for testing, you must have at least 4 polls with each poll having from 2 to 4 choices, and randomly provide responses for some of the choices in these poll. Make sure you have some published and unpublished polls. Use the admin interface username: `test`, password: `123123`
- [ ] **(5 pts)** Create a view to list all the posts which have a **published** status, show the poll title and date it will be active until.
- [ ] **(5 pts)** Create a view to list all the posts which have a **unpublished** status, show the poll title and date it will be active until.
- [ ] **(10 pts)** Create a view to show the details of a single poll (all information about the poll), including the question and all the choices available.
- [ ] **(5 pts)** Create a view to list the names of everyone that selected a specific choice in a poll and the time they submitted their response
- [ ] **(5 pts)** In the poll list view, make the title of each poll into a link that opens the corresponding poll's detailed view when clicked.
- [ ] **(5 pts)** In the poll list view, show number of options for each poll.
- [ ] **(5 pts)** In the detailed view, show the total number of responses, and for each response, show how many people chose that response.
- [ ] **(5 pts)** In the detailed view, turn each choice into a link if clicked will open the view the lists the names of everyone that made that choice.


### Bonus Tasks

These tasks will involve reading the Django documentation and figuring out things on your own. Perform these tasks only after you complete the previous requirements of the assignment.

- [ ] **(5 pts)** Use the same URL pattern for both the published and unpublished poll list view to display them both instead of having separate entries in urls.py
- [ ] **(5 pts)** In the view that lists responses, instead of showing date/time show the time since the response was submitted. For eample, **submitted 10 days, 6 hours, 5 minutes ago**. Search Django's template filters to find the solution. It should be a very simple one. 
- [ ] **(10 pts)** Read about the [bootstrap CSS framework](https://getbootstrap.com/docs/5.0/getting-started/introduction/) and try to use it to improve the look and feel of your application
- [ ] **(20 pts)** Get a head start and read this [Django forms tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms), try to create a view that allows users to submit their responses **(HINT: You will also need to read about ModelChoiceField)**


## How to Start and Submit Your Project

1. Join the [poll-project part2 assignment on github classroom](https://classroom.github.com/a/X5Kr-4oh).
2. Click on the **Work on Replit** button on the readme file to import a private project for the assignment.
   - IMPORTANT: The repl may crash as you import the project, you will have to go to "my repls" and re-open the repl and it should work fine.
3. Add the file bonus.md and list all the additional bonus tasks you completed in your assignment.
4. When done, commit and push your work to GitHub. You can continue to make changes and push code after submission.
