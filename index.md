<link rel="stylesheet" href="./style.css">

# Team UHp!

## Table of contents
- [Overview](#overview)
- [Deployment](#deployment)
- [User Guide](#user-guide)
- [Developer Guide](#developer-guide)
- [Continuous Integration](#continuous-integration)
- [Development History](#development-history)
- [Team](#team)
- [Contact Us](#contact-us)

## Overview

Many college students want to build real-world experience and strengthen their resumes through hands-on projects. However, the scope and complexity of meaningful and large-scale projects may exceed their current technical skills or confidence. Such a gap makes it difficult for students to initiate or complete projects that truly showcase their abilities.

TeamUHP! is a platform for students to connect across areas of study by enabling them to upload project postings and recruit collaborators. Whether it’s a class assignment or a passion project, students can find teammates with complementary skills and allow each contributor to play a meaningful role that aligns with their field of study. This medium of collaboration helps students to gain practical experience, build teamwork skills, and add completed projects to their resumes.

## Deployment

The TeamUHp! web application is deployed through Vercel cloud platform and hosted at [team-uhp.vercel.app](https://team-uhp.vercel.app/).

## User Guide
This section provides a walkthrough of the TeamUHp! user interface and its capabilities.

**Landing Page** <br>
<!-- TO DO: Update "Helpful Tools page" as described in this paragraph -->
The landing page is presented to users when they visit the website. Clicking any of the internal page links without being signed in redirects the user to the Sign In page. Clicking the Helpful Tools link will take the user to a collection of external site links Team UHp thinks you might find helpful. Clicking the About Us or Resources links in the footer will redirect the user to those pages without requiring signing in.
<img class="padded" src="images\pages\landing-page.png">

**Sign In Page** <br>
The sign in page allows users to sign in and provides links for creating a new account or requesting a link to reset forgotten password.
<img class="padded" src="images\pages\viewer-sign-in-page.png">

**Forgot Password Page** <br>
If a user has forgotten their password, they may reset it by inputting the email associated with their account, and receive an email from TeamUHp automation (team.uhp.automation@gmail.com) to reset the password.
<img class="padded" src="images\pages\forgot-password-page.png">

**Sign Up Page** <br>
If a user has no yet created an account, they may sign up using UH email address. After filling in the necessary account information, an automated email is sent to verify the account. The user must check their email to follow the link to verification. All automation links are sent from the team's automation contact: team.uhp.automation@gmail.com.
<img class="padded" src="images\pages\viewer-sign-up-page.png">

**List Projects Page** <br>
<!-- TO DO: Include filtering (by due date) capabilities mentioned in this paragraph -->
The project list provides clickable summaries for all active projects. The list is sorted by number of skills that the user and each project have in common.
<img class="padded" src="images\pages\project-list-page.png">


**Add Projects Page**
Clicking on the "Add Project" button from the Project List page, users can post a project by filling in Ttitle, description, and due date of the project. Line breaks in the description input are preserved when displaying the description on the project page. 
<img class="padded" src="images\pages\add-project-page.png">

**Project Page** <br>
Each individual project page displays the project's details. The project page provides the project image/banner, title, description, project members, openings on the project, and the skills sought across all openings. Clicking on openings will take users to the opening page. If no image is provided during the Project's Creation, a default banner is displayed.<!-- "Default Banner" subject to change after photo sharing solution --> When logged in as a project's admin, the subsequent button "Recruit for Opening" is visible:
<img class="padded" src="images\pages\owner-project-page.png">

**Opening Page** <br>
End users looking for projects will view a project page, then click on a specific position opening. The specified posiiton is detailed on its own page and provides the title, description, and skills sought of the project opening. Users can click the link to apply for the position.
<img class="padded" src="images\pages\opening-page.png">

**Add Opening Page** <br>
The add opening page is used for project posters to open positions for members they seek to recruit. They can specify the title for the position, add a description for project tasks, select specific skills needed for the position, and schedule the dates for which the project is open to contributors:
<img class="padded" src="images\pages\add-opening-page.png">

## Developer Guide
First, install a code editor

Second, go to the Team-UHp page, and select the "use this template" button to create a repository with Team-UHp as a template.

Third, upon opening your new program, cd into the Team-UHp/app directory, and install libraries by typing into the terminal:

<code>$ npm install</code>

Fourth, run the system with the command:

<code>npx prisma migrate reset</code>

If successful, you should see the application appear at http://localhost.3000

**Database Editing** <br>

To launch the prisma database editor on your web browser, run the command:

<code>npx prisma studio</code>

For your .env file:

make sure to comment vercel directUrl 

<code>
datasource db {<br>
&nbsp;&nbsp;provider = "postgresql"<br>
&nbsp;&nbsp;// for local development<br>
&nbsp;&nbsp;url       = env("DATABASE_URL")<br>
&nbsp;&nbsp;// for Vercel, uncomment<br>
&nbsp;&nbsp;// directUrl = env("POSTGRES_URL")  <--- Comment this to run locally at localhost:3000<br>
}
</code>

**Gmail Automation Setup** <br>

This guide is not intended for professional applications. This guide is accurate as of November 30, 2025. Gmail may not permit extensive commercial use of its services without paying for the right to do so. This method is not nearly as secure as using OAuth 2.0 and google's API. Caveat emptor.

<img class="padded" src="images/gmail-how-to/01.png" alt="Gmail Setup 1">

0\. Create a Gmail account with the name you want your app to be sending messages under. It is strongly recommended that this be professional, related to your app or company name, and include "noreply" in some form if you are not going to check the inbox for messages. The account must also have 2-Step Verification enabled.

1\. Visit [accounts.google.com](accounts.google.com)

2\. Click Go To Google Account.

<img class="padded" src="images/gmail-how-to/02.png" alt="Gmail Setup 2">

3\. Click Security & sign-in.

4\. Type "app password" in the search bar.

5\. Click App Passwords in the dropdown.

<img class="padded" src="images/gmail-how-to/03.png" alt="Gmail Setup 3">

6\. Type the nickname you want the password to be referred to as. This is not used anywhere except this list, so ensure the name will remind you what app it is for.

<img class="padded" src="images/gmail-how-to/04.png" alt="Gmail Setup 4">

7\. Save this password. You will not be able to access it again once you close the popup.

8a. If you are running the app locally: in your .env file, type the following information (replace with your account information):

    #EMAIL_HOST=smtp.gmail.com
    GMAIL_USER=team.uhp.automation@gmail.com
    GMAIL_APP_PASSWORD=prdwvhtwzesvevtj
    
Note that the app password you generated earlier has no spaces.

8b. If you are running the app on Vercel: Go to your app, Settings, Environment Variables, and add your GMAIL_USER and GMAIL_APP_PASSWORD variables to the list.

## Continuous Integration
![ci-badge](https://github.com/team-uhp/team-uhp/workflows/ci-team-uhp/badge.svg)
<!-- TO DO: Badge will work once main repository ci.yml is renamed to ci-team-uhp -->

TeamUHp implements continuous integration using GitHub Actions, such that all commits into the main branch trigger a build of the system and the running of ESLint checks and all Playwright tests. Results of all recent workflows are viewable at https://github.com/team-uhp/team-uhp/actions. 

The workflow definition file is located at .github/workflows/ci.yml.
## Development History
The development process for TeamUHp conforms to Issue Driven Project Management (IDPM) practices. In this model: 
- Development consists of a sequence of Milestones.
- Each Milestone is specified as a set of tasks.
- Each task is described using a GitHub Issue, and is assigned to a single developer to complete.
- Tasks should typically consist of work that can be completed in 2-4 days.
- The work for each task is accomplished with a git branch named “issue-XX”, where XX is replaced by the issue number.
- When a task is complete, its corresponding issue is closed and its corresponding git branch is merged into master.
- The state (todo, in progress, complete) of each task for a milestone is managed using a GitHub Project Board.
- The following sections document the development history of BowFolios.

**Milestone 1: Mockup development** <br>
The goal of Milestone 1 was to create a set of HTML pages providing a mockup of the pages in the system.

Milestone 1 was managed using [TeamUHp GitHub Project Board M1:](https://github.com/orgs/team-uhp/projects/1)

<img class="padded" src="images/milestones/m1.png" alt="Milestone 1">

**Milestone 2: Improved Functionality & UI design** <br>
The goal of Milestone 2 is to improve functionality and quality of the application, including functionality of mockups created in M1, adding mockups to that supplement to existing pages, and finalize the overall design of the landing, projects, openings, and form pages.

Milestone 2 was managed using [TeamUHp GitHub Project Board M2:](https://github.com/orgs/team-uhp/projects/3)

<img class="padded" src="images/milestones/m2.png" alt="Milestone 2">
<p style="text-align: center; font-style: italic;">Current milestone in progress.</p>
<!-- TO DO: Update Milestone 2 to completed preview of Project @M2 by deadline  -->

**Milestone 3: Improved Functionality & Supplementary Features** <br>
The goal of Milestone 3 is to complete near-final functionality of critical features, and complete implementation of supplementary features that were added in design. 
<!-- TO DO: Include milestone 3 description -->

Milestone 3 is managed using [TeamUHp GitHub Project Board M3:](https://github.com/orgs/team-uhp/projects/6)

<img class="padded" src="images/milestones/m3.png" alt="Milestone 3">
<p style="text-align: center; font-style: italic;">Next milestone to follow.</p>
<!-- TO DO: Add milestone 3 image -->


## Team
[Team Contract](https://docs.google.com/document/d/1vcm45B1ehz_Joi1jSSsUXPrAqlw8uORYBjaiFehP7uw/edit?usp=sharing)<br>
TeamUHp! is designed, implemented, and maintained by Jayden Francoise, Matthew Matsumoto, Raymond Acker, Joan Zara, and Jun Xiang (Juno) Zeng.

<div class="team">
  <div class="member">
    <img src="images\members\jaydenfrn.jpg" alt="Jayden Francoise">
    <h3>Jayden Francoise</h3>
    <a href="https://jaydenfrn.github.io/">jaydenfrn.github.io</a>
    <p>Computer Science Student at University of Hawaii at Manoa</p>
  </div>

  <div class="member">
    <img src="images\members\matthewmatsumoto.jpg" alt="Matthew Matsumoto">
    <h3>Matthew Matsumoto</h3>
    <a href="https://matthewmatsumoto.github.io/">matthewmatsumoto.github.io</a>
    <p>Computer Science Student at University of Hawaii at Manoa</p>
  </div>
  
  <div class="member">
    <img src="images\members\ackerrs.jpg" alt="Raymond Acker">
    <h3>Raymond Acker</h3>
    <a href="https://ackerrs.github.io/">ackerrs.github.io</a>
    <p>Computer Science major at UH Manoa, rock climber, and avid reader</p>
  </div>

  <div class="member">
    <img src="images\members\jn1za.jpg" alt="Joan Zara">
    <h3>Joan Zara</h3>
    <a href="https://jn1za.github.io/">jn1za.github.io</a>
    <p>Computer Science Student at University of Hawaii at Manoa</p>
  </div>

  <div class="member">
    <img src="images\members\junoxzeng.jpg" alt="Jun Xiang (Juno) Zeng">
    <h3>Jun Xiang (Juno) Zeng</h3>
    <a href="https://junoxzeng.github.io/">junoxzeng.github.io</a>
    <p>Computer Science Student at University of Hawaii at Manoa</p>
  </div>
</div>

## Contact Us
The team email is team.uhp.automation@gmail.com. Alternate forms of contacting members are available on our individual github.io profiles above.
