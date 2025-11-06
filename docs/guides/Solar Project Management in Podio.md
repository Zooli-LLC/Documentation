Podio's power and ease of customization make it an ideal platform for solar installation businesses. There are software services built specifically for this purpose, but they force you into their own structure instead of allowing you to custom build your own.

This guide will show you how to set up a basic template for your solar business, with suggestions on further customizing it to maximize efficiency and seamlessly fit your team's processes. The template is built to maximize efficiency while helping your team stay on top of their tasks.

**Don't want to build the apps and flows yourself? [Contact us](https://forms.momentumtools.io/?form=lqjomvmsqiir&services-requested=5&what-would-you-like-to-purchase%5b2%5d=true) to purchase the starter template shown here for $1000.**

As you browse the guide, keep in mind this is just one of many ways you can set up Podio for your solar business. If you would like something more custom for your existing processes, we also offer [**personalized setup assistance**](https://forms.momentumtools.io/?form=lqjomvmsqiir&services-requested=2) for a more custom-tailored workspace.

If you are still deciding if Podio is the right tool for you, we recommend looking at the structure of the apps here, and then skimming the Podio Workflow Automation section at the bottom to get an idea for how a project will flow from start to finish.

**Here are the apps used in our template workspace:**

**Projects**

![Screenshot](/images/example_solar_apps.png)

First, we use a **Projects** app as the container for all information related to the project, with separate apps for scheduled events such as site surveys and installations. We have chosen to separate these events to help keep things organized yet easily accessible. If you track too many different things all from one app, it can be very difficult to find the information you need, and the app's performance will be degraded as well.

The Project app contains section headers to divide up the various aspects of the project. 

A sample project:

![Screenshot](/images/example_solar_project.gif)

**The Project App sections are as follows:**

- **Customer Information:** The customer's contact info and property address for the solar installation

- **Project Details: **Information about the project such as panel type, number of panels, any special additions, etc.

- **Sales/Finance Information: **Who sold the deal, how much did the customer pay, and how they are paying for it.

- **Project Stages:** The sections contains links to the scheduled events for the projects: Permit applications, Site Surveys, Installations, and Inspections. These links can be clicked to view more details on each event.

**Database app**

In addition to linking to separate stage apps, we have also created a **Database app** to store the various types of equipment and other information that you will select from the Projects app. This app stores the following:

- Inverter models

- Solar panel models

- Battery models

- Finance companies

You can store anything else here as well - just add a new Category field via the [app template](https://help.podio.com/hc/en-us/articles/201019578-Modifying-an-app) to keep everything organized by type.

**Common Question:** Why use the Database app instead of adding category fields in Projects for Panels/Inverters/etc?

- While Category fields are certainly an option, using a Relationship field is usually the better choice in these cases, as there can be dozens of models for each equipment type. Using category fields for anything that requires more than 20 categories is generally not recommended, as they can slow  down your app and also do not allow you to search to easily find the value you need.

- Additionally, as models are replaced with newer versions, you can keep historical data by marking equipment types as Active or Inactive. Your relationship field in Projects can be set to show only the active equipment:

![Screenshot](/images/example_solar_relationship.png)

**Scheduling Apps: Site Surveys, Permits, Installs and Inspections**

A major benefit to keeping these apps separate is that you will typically have different teams in each respective event type, and this gives a clean and straightforward area for those teams to go to find their scheduled events.

Team members can use [filters](https://help.podio.com/hc/en-us/articles/201019638-Views-filters-and-reports) to show only the items assigned to them.

You can also use the "Show in calendars" option to ensure that team members will see their events from their [Podio calendars](https://podio.com/calendar).

![Screenshot](/images/example_solar_calendar.png)

**Task app**

This is an optional app to assign tasks to your team members. Some prefer to use [Podio's built-in task system](https://help.podio.com/hc/en-us/articles/201019558-Overview-of-tasks), but this is meant for quick to-do's and lacks reporting, customization, and collaboration options.

The tasks app is linked to the Projects app, and can be [modified](https://help.podio.com/hc/en-us/articles/201019578-Modifying-an-app) to link to any other app as needed. We recommend setting up Workflow Automation flows to create tasks here on certain triggers, such as an install being scheduled or a new project being assigned to a Project Coordinator.

**Podio Workflow Automation suggestions for template workspace**

Consider these as a few examples of what is possible in automating your space, but ultimately you decide which flows and processes work the best for your team.

**Projects**

- On Project creation, [assign a Project Coordinator via round robin](https://tutorials.zooli.io/hc/en-us/articles/360035354434-Building-a-Round-Robin-Assignment-Flow)

- When a project stage changes to Site Survey, Permit, Install, or Inspection, create a new item in the respective app and link it to the project

- When a project moves to the Install stage, assign a task to the Project Coordinator to set up an install date and time with the customer

- When a project moves to the Inspection stage, assign a task to the Project Coordinator to set up an inspection date and time

- When a project moves to the PTO stage, assign a task to the Project Coordinator to notify the customer

- If a project has been in the same stage for 2 weeks, create a task for the Project Coordinator to review. This helps prevent projects from falling through the cracks

**Site Surveys**

- On the day before a site survey, send an email to the site surveyor with the appointment information

- On the evening of the site survey, if the site surveyor has not yet added any notes, send them an email reminding them to add their notes from the appointment

- When the Site Survey is complete, set the Project stage to Design and assign a task to the Design team

**Permits**

- When the status changes to "Permit Obtained," update the Project stage to Install (also triggers flow above in Projects, notifying the Project Coordinator to schedule the install)

**Installs**

- On the day before an install, send an email to the install crew manager with the install information

- On the evening of the install, if the install has not been marked as complete, send the install crew manager an email reminding them to update the installation item in Podio

- When the install is complete, set Project stage to Inspection (triggers above flow in Projects, notifying the Project Coordinator)

**Inspections**

- On the day before an inspection, send an email to the inspector with the inspection information

- On the evening of the inspection, if the inspection was not marked as either "Passed" or "Issues Found," send an email to the inspector reminding them to update the installation item in Podio with the inspection result

- When the inspection is complete, set Project stage to Awaiting PTO

**Tasks**

- On a task's due date, if incomplete, @mention the task assignee to remind them about the task
