# ReserveTrack 
ReserveTrack is a simple web-based time tracking application to be used by reserve police officers.   A reserve officer is a volunteer police officer.   Departments need to keep track of their service, but cannot use the time card systems used by paid officers.  

The application has 4 distinct functions: 1- Login & Registration, 2- Time entry, 3- Reporting, 4- Administration.

This site will primarily be used on mobile phone browsers and must be functional with Chrome and Safari. 

Technical platform is:
UI: HTML5 and Bootstrap.  
Application Server: Python Flask
Database: Postgres 11.x

## Login and Registration
On accessing the web site, the user must be presented with a login screen to enter username and password.  These credentials must be validated against the user store.

All users can enter time, some users will have admin rights.  The two classes of users are "Officer" and "Admin".

## Time Entry
Each user will have a time entry screen that collects data for time spent on duty. A user must be able to edit a time entry they have already submitted.
 
This screen should 

Initial Categories include:
* Patrol Assigned
* Patrol Voluntary
* Community Relations
* Administrative
* Training
* Meetings

The time entry form should default the category drop-down to "Patrol Assigned"

The user

*Time Entry Validations*
1. The date and time must resolve to a valid date time value in the database.
2. The end date must be after the start date.
3. The category must be selected.
4. The duration must not exceed 24 hours.
5. The entry must be successfully inserted into the database.
6. The user must get a confirmation following successful insertion into the database.

*Time Entry Security*
A non-administrator user can only enter time entry records for themself.   

An Officer user can edit their own entries but cannot edit other Officer’s entries. 

An Administrator can add and edit their own records and the entry of any other user.  

An Officer user can delete their own time entry record, but not the record of any other user.  An Administrator can delete any time entry record.  

*Design Expectations*
* The time entries should be navigable using a RESTful path. 
* An API is not required at this time, but the design should support a future work to build an API. 
* The UI should be a simple UI that renders well on a phone browser and on a desktop browser.  


## Reporting
The reports function has two simple displays.

1-  Leaderboard
The leaderboard is a horizontal bar chart with 1 bar for each user for the selected date range.  Each bar is the sum of hours entered into the Tine Entry table for that user.   The bars are sorted with highest sum at the top and lowest sum at the bottom. 

This page has a drop down control allowing the user to pick one of the following sections:
* This week 
* Last week
* This month
* Last month 
* Year to date

2- User Time Entry Report
This page is a simple list of all time entered for the selected users for the selected date range. 

The data must be displayed in a table with the following columns:
* User
* Start Date and Time
* End Date and Time
* Duration
* Category

The report must include the following filter controls that limit the rows returned:
1. Start Date - a valid date
2. End Date - a valid date
3. User - a multi-select control allowing selection of multiple users.  

## Administration 
The administration section provides 2 functions:

1- User Administration 
This page should be a list of users and the ability to add a user.  

On adding a new user

## Database and Database Schema
The database must be a Postgres database.  See below for site hosting requirements.

Developers have discretion on the final data model, but a 3 table structure is envisioned:

*User*
This table stores user ID, username, encrypted password, role, create date, last login date, force_password_change

Password values must never be stored in plaintext, they must be bcrpyt encrypted or approved comparable algorithm. 

*Time Entry*
The Time Entry table stores: User ID (Foreign Key to the User table), start dateline, end date time, category (Foreign Key to the Category table), duration (calculated as the time delta between start and end dates), and note.

*Category*
A table listing the time entry categories.  ID and Label.

### Site Hosting Requirements
The site will be hosted on Heroku. 
The database will be hosted on a Heroku Hobby Postgres instance (https://www.heroku.com/postgres).   The deliverables must include the deployment and configuration scripts to setup and deploy this instance.

