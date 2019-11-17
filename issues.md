# ReserveTrack bugs
*Issue #1  Time Entry must allow date time values in the past.*  (tested on desktop Chrome)
The Start time allows selection of a prior date, but the end time only allows current date and an hour setting that is after the hour setting of the start time.
    
https://www.dropbox.com/s/k52jq89d4mx2qx8/Screenshot%202019-11-16%2020.35.27.png?dl=0  end time hour does not allow hours before the start time hour.   This may prevent second shift entries where the start time is 19 and the end time is 3.

https://www.dropbox.com/s/dehciq06ym5actw/Screenshot%202019-11-16%2020.38.38.png?dl=0 calendar date cannot be in the past for end time.

https://www.dropbox.com/s/nfl6kocn81y59un/Screenshot%202019-11-16%2020.41.43.png?dl=0 End time date selection does not allow selection of a day of the month.

https://www.dropbox.com/s/6pjfdc90z2587ux/File%20Nov%2016%2C%209%2000%2034%20PM.jpeg?dl=0 End time selection disabled on iOS Safari.  A user must be able to enter a start time and an end time in a single entry, or a start time with the ability to enter an end time later.  In other words, we must support the user who forgot to enter time and now just needs to record time worked in the past.

Officers may forget to enter time at the start of their shift.  They need to be able to enter a time entry for any start date and any end date.  We can keep the 24 hour max duration rule.   Users must be able to enter a start time and an end time in the future.  The start time may be on a prior calendar day than the end time (as long as the total duration is not more than 24 hours.)  The end datetime must be after the start datetime.

Admin users must be able to edit the time entry of any user and must be able to submit a time entry for any user.

*Issue #2  Page banner covers left menu on mobile* (tested on iOS Safari)
https://www.dropbox.com/s/hzreehu69xh3nc5/IMG_0837.PNG?dl=0  When swiping right, the blue banner at the top of the screen covers up the menu options.


I*ssue #3  Mimetype on user report download is not set correctly* (tested on MacOS Safari)
The Users EntryReport shows csv data in a browser screen.  This should be a csv or xlsx file to the browser download function.

*Issue #4 Time entry for deleted users is not visible in the Time Entry admin screen* (tested on MacOS Safari)
The UserTime Entry report shows entries for user "John Doe" but the Time Entry data table does not list these entries.  The admin user must be able to see all time entries in the database.

*Issue #5 Admin user editing the time entry for another user can create an entry that is longer than 24 hours.*
Enforce the 24 hour rule when an admin is editing a time entry.
Steps to reproduce:
1. Login as admin
2. Go to Time Entry
3. Select the edit link for an existing time entry.
4. Enter an end time that is greater than 24 hours after the start time.


*Minor UI changes*
- (see below) Change "Pin Code" on the Add User screen to "ZIP Code"
- Hide all non-required fields on the Add User screen.
- Remove the "01" option from the minute drop down on the time entry screen.
- Update the copyright in the footer to 2019 instead of 2018.
- The Leaderboard should not show admin users.
