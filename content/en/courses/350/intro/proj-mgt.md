---
# Page title
title: Project Management

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Project Management

# Page summary for search engines.
summary: Second programming course for MIS majors utilizing Python to build data-driven business applications.

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 4

draft: False
diagram: True

---

Project management is about ensuring that the project is completed to specification and within time and resource budget. This involves ensuring each team member knows what they are supposed to do.

We will depart from traditional project management and use a more agile approach. The main difference is that with agile development:
- Requirements are expected to change, therefore we use different tools to track requirements and focus on priorities.
- Customers and developer involvement in project management is necessary for success. Developers must have initiative to choose the tasks they work on and participate in updating requirements and report progress on their work. 

The project manager's role is also changed slightly:

- Might contribute to the project like any other developer would, by working on requirements and suggesting new ones.
- Ensures that there are enough tasks to keep everyone busy
- Guide the project by prioritizing tasks, monitoring progress, and resolving problems.
- We will also give the project manager the responsibility of merging the work of team members into the project. Different teams might choose different workflows.
- Setting up the project environment where team members can collaborate.

### Creating a GitHub Project/Repo

There are two main ways in which a project manager can create a project:

1. Creating a new empty repository either from GitHub or pushing a new project from Replit.com to GitHub.
2. Forking an existing project found on GitHub, which would allows the team to build on this existing project.

Once a project is created, it would be a matter of coordinating with team members and assigning tasks and collaborating to ensure the project delivers the system it was intended to build. GitHub offers a number of useful tools to enable project managers to manage projects, which we will discuss in the next section.

## Project Management Tools

Once the project is setup the following tools are available that both the project manager and team members use to coordinate:

### 1. GitHub Issues

A GitHub issue could represent many things in a software project. Whether its a feature that needs to be built, a bug that needs fixing, an idea to be discussed, documentation to be written, or any other task (programming or coordination or other) that the project team needs to complete or discussed can be represented using a GitHub issue. The following figure shows an example project on GitHub called **Ruby on Rails** where hundreds of developers collaborate. You can see how some issues describe problems that need fixing and other are feature requests. Some have discussions associated with them and some are just there waiting for a developer to start working on them:

{{< figure src="courses/350/issues.png" caption="Example Issue List from Ruby on Rails Project" >}}

A good way to start start the issues list is to convert the project requirements into a list of issues on GitHub. But when you do that, you must ensure that each issue describes a very specific task. Team members would look at the issue list and identify a task that they could work on. For example, the project used to translate the current website has the following issue list:

{{< figure src="courses/350/translate-issues.png" caption="Example Issue List from Ruby on Rails Project" >}}

You can see the list is very simple, given that the project is simple. Each issue represent the translation of a single file. This would be a very useful coordination tool between team members, as one member can choose to translate one of the files by assigning the project to themselves. This would let other members know that this task is being worked on one of their team mates and they need to look for another task to complete. Project Managers can also choose to assign the issue to specific members so they would know that the task is their responsibility. The following figure shows how tasks can be assigned:

{{< figure src="courses/350/translate-issues.png" caption="Assigning an Issue to A Team Member or to Yourself" >}}

{{% callout note %}}
Make sure that you always assign your self a task before you start work on a task. If the task is not in the list, then create it. This would allows your team members to know what you are working on.
{{% /callout %}}

The issues list is a dynamic list. It should be changing on a daily/weekly bases if the project is active. It since the issues represent requirements, it also reflects how the requirements are constantly changing as the issue list is updated.

#### Who Writes The Issues?

The responsibility of writing the issues is shared between the project manager, the developers, and even the users of the project. If a member has a new idea that they need to be written, or if they discover a bug that needs fixing, then they capture this by creating an issue and describing the idea or problem. The project manager needs to ensure that there are enough issues in the issue list for the team members to find work to complete, the project manager is also responsible for prioritizing the work. But priority of issues is not shown here, it is shown in the project board which we will explain next.

{{% callout note %}}
Whether you are the project manager or a member in the team, you can create issues to capture ideas bugs and tasks you want the team to work on. 
{{% /callout %}}

### 2. Project Board

The project board gives a visual overview of how the project is progressing. The project tasks (known as issues on GitHub) are shown as tickets. Therefore, we will use the terms **issue, task, and ticket** interchangeably. The tickets are organized in three different columns as follows:

1. **To do:** Newly created tickets are placed here which no one is working on. This includes bugs and new features that developers might want to incorporate in the project. Tickets placed at the top of the column have higher priority, and it is the responsibility of the project manager to organize these tickets by priority in this column. Developers are encouraged to pick tickets to work on from the top of the **to do** column.

{{< figure src="courses/350/project-board.png" caption="Project Board Showing the Columns and Tickets" >}}

2. **In Progress:** Tickets claimed by members to work on must be moved here by the member working on them, so that the project manager will know what is being worked on. The following clip shows you how to claim a ticket for your self to work on:

![](/gifs/claim-ticket.gif)


3. **Done:** Completed tickets are moved here, where project manager will know that there is a pull request that needs to be merged. Once the pull request is merged the ticket is archived. Simply drag the ticket you completed from **In Progress** column to **Done** column and do not forget to create a pull request.


{{% callout note %}}
The project manager should order tickets in the To To list by priority from top to bottom. Team members are encouraged to select tickets to work on from the top of the To Do List.
{{% /callout %}}

Provided team members move the tickets correctly from one column to another, the project manager will easily get a general idea of who is working on which task. A ticket remaining for a very long would signal that there is a problem with that task or the member working on it. This will require the intervention of the project manager.

**Weekly or Bi-Weekly coordination meetings:** It would be very helpful of a team would meet on a weekly or bi-weekly bases where the project board is shown and priority of To Do tickets are discussed and any challenges facing the project. Members could also work together towards finding common solutions or suggest new tickets to include in the to do list..

## Tips on Writing Issues/Tickets

The best method to write useful task descriptions is to write issues/tickets as **user stories**. User stories describe the functionality of a system and the tasks to work on from the perspective of the user. It details what the user does and why. A single user story should describe a single functionality. If the functionality is complex, then you can break it down into smaller user stories.

The following [blog post on how to write user stories](https://medium.com/innovation-machine/how-and-why-to-write-great-user-stories-f5a110668246) is an excellent start for anyone looking to improve how they write tickets for a software project.


## Review Questions

- How would you use tickets in your development project?
- What is the role of a project manager?
- What role do team members, other than the project manager, play in project management?