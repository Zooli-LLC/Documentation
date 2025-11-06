This guide will show you how to manage your recruiting processes with Podio and Workflow Automation. This workspace is built to let Podio and Workflow Automation handle the busy work, allowing you to focus your time on finding the perfect candidate to join your team.

**Don\'t want to build the apps and flows yourself? [[Contact us]{.underline}](https://forms.momentumtools.io/?form=lqjomvmsqiir&services-requested=5&what-would-you-like-to-purchase%5b3%5d=true) to purchase the starter template shown here for \$400.**

**Watch the video:**

The workspace is set up with 3 apps: **Requisitions**, **Candidates**, and** Interviews**. The apps are all tied to one another via relationship fields, giving you a clear view into everything that is going on for your open positions and for the candidates applying for them. 

**Requisitions**

This app contains all of your job openings and all of the details that go with them. In addition to the information around the job opening, you can also find all applicants for each position via the \"Related Items\" section at the bottom.

The Requisitions app contains the following fields:

**Job Title:** Text field (single line)

**Job Description: **Text field (multi line)

**Status: **Category field with options:

- Active

- Offer Sent

- Offer Accepted

- Archived

**Hiring Manager: **Member field

**Listings: **Link field

**Salary Range: **Text field (single line)

**Notify Applicants: **Category field

- This field triggers a Workflow Automation flow, which sends an email to all candidates who were not selected for the position.

**Candidates**

This app will capture the applicant details for your job listings. This is where you will review each of the candidates who has applied for your open requisitions and track their status through the hiring process. We recommend setting up [[filters]{.underline}](https://help.podio.com/hc/en-us/articles/201019638-Views-filters-and-reports) in this app to efficiently manage the candidates you are reviewing. For example, you can set up a filter that shows only the unreviewed candidates for a specific job opening:

![A screenshot of a computer
AI-generated content may be incorrect.](media/image1.png){width="6.5in" height="4.959027777777778in"}

After setting up the filter, you can click on any candidate and then use the arrow keys on your keyboard to quickly review each candidate in your filter. 

The candidates app has the following fields: 

**Full Name**: Calculation field combining the First and Last name fields below. This is optional - you can also choose not to separate first and last names, and instead store them in just one text field called Full Name.

**First Name**: Text field (single line)

**Last Name**: Text field (single line)

**Phone Number**: Phone field

**Email Address:** Email field

**Applying For**: Relationship field pointing to the **Requisitions** app

**Source:** Category field with options:

- Internal Referral

- External Applicant

- Internally Sourced

Note that this is an optional field, and sources can be added or removed as well.

**Status**: Category field with options:

- Applied

- Scheduled Phone Interview

- Scheduled In-Person Interview

- Offer Sent

- Offer Accepted

- Rejected

As noted above, the options in this field can also be customized to fit your own processes.

**Cover Letter:** Text field (multi line)

**Interviews**

Just like it sounds, your interviews will be scheduled in the Interviews app. This app is an **Event type app** which allows interview attendees to RSVP to their interview. You can also set up a GoToMeeting or Appear In videoconference if the meeting will take place remotely:

![A screenshot of a video call
AI-generated content may be incorrect.](media/image2.png){width="6.5in" height="2.41875in"}

When you invite your candidate to the Interview item in Podio, they will receive an email invitation with an RSVP option. The email will also contain a calendar invitation so that the interview date and time will automatically be added to their calendar. 

![A screenshot of a chat
AI-generated content may be incorrect.](media/image3.png){width="6.5in" height="4.777083333333334in"}

Note that this also gives the candidate access to the Interview item in Podio, so you should not store any internal information here. We recommend keeping your notes on the interview in the **Candidate **app item instead.

The Interviews app contains the following fields:

**Title**: Calculation field combining the candidate\'s name and the position they are applying for (e.g. \"Lauren Byerly for Technical Writer\")

**Candidate**: Relationship field pointing to the **Candidates** app

**Position**: Relationship field pointing to the **Requisitions** app

**Interview Type**: Category field with options:

- Phone

- In-Person

**Interview Date**: Date field with time entry and end date enabled

**Participants**: Member field, this is a requirement for Event type apps in order to enable RSVP

**Meeting Notes**: Text field (multi line). **Remember that the candidate will have access to this, so this is not for internal information. **We recommend using this for parking information, dress code, and anything else the candidate will need to know in order to prepare for their interview. 
