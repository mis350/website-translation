---
# Page title
title: The Poll Project 3nd Assignment

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Part 3

# Date page published
date: 2021-06-06T14:29:57Z

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 50

draft: false

---

{{% callout note %}}
Due Date is <strong>Tuesday June 15th before 1st lab</strong>
{{% /callout %}}

## Requirements for This Assignments (50 pts)

- [ ] **(10 pts)** Create a view to create a poll that redirects you back to the poll list upon successful completion
- [ ] **(10 pts)** Create a view to add a single option to a poll. The view should display the poll, existing options, and a form to add one more options. The view should redirect you to the same view upon successful completion so you can add more options if you choose to (HINT: You have to use redirect to force the client to reload the page with an empty form for creating the poll)
- [ ] **(10 pts)** Create a view that creates a response associated with a selected option. The view should display the poll and the chosen option. The submit button label should be "Confirm Choice". (Hint: The selected option should be specified in the URL, for example, respond/option/5, means that the user chose to select option with id 5). Upon successful creation of response, redirect the user to show the detailed view of the poll.
- [ ] **(10 pts)** Create a view that allows you to edit the poll question and details **without** the options, upon successful completion should redirect you to the detailed poll view. The view should list the available options but no need to make them editable.
- [ ] **(10 pts)** Create a view that allows you to edit a single poll option, upon successful completion should redirect you to the detailed poll view


### Bonus Tasks

These tasks will involve reading the Django documentation and figuring out things on your own. Perform these tasks only after you complete the previous requirements of the assignment.


- [ ] **(5 pts)** In the poll list view, add a link at the bottom of the list to create a new poll, link it to the create poll view
- [ ] **(5 pts)** In the poll detailed view, add a link next to the poll question for editing the poll
- [ ] **(5 pts)** In the poll edit view, convert the options into links that allow you to edit the option. When they are clicked, they send you to the edit option view.
- [ ] **(5 pts)** In the poll edit view, add a link below the options to add another option that sends you to the option adding view
- [ ] **(5 pts)** In the show poll view, put a "vote" link next to each option that will send you to the create response view
- [ ] **(10 pts)** For the links, instead of typing the path yourself, give the path names and use the [url template tag from Django](https://docs.djangoproject.com/en/3.2/ref/templates/builtins/#url)
- [ ] **(20 pts)** In the show_poll view, add a form to allow for users to post comments about the poll. Do not forget to create a model for the comments that must be associated with a poll. The comment should allow user to enter his name, email, and text of the comment. The comments should be displayed above the comment form in chronological order, which is why you must record the time the comment was created also.
- [ ] **(5 pts)** If you have successfully used bootstrap, try to convert all the link for editing bootstrap to look like buttons


## How to Start and Submit Your Project

1. Join the [poll-project part3 assignment on github classroom](https://classroom.github.com/a/0JE2Bq4p).
2. Click on the **Work on Replit** button on the readme file to import a private project for the assignment.
   - IMPORTANT: The repl may crash as you import the project, you will have to go to "my repls" and re-open the repl and it should work fine.
3. Add the file bonus.md and list all the additional bonus tasks you completed in your assignment.
4. When done, commit and push your work to GitHub. You can continue to make changes and push code after submission.
