This tutorial will show you how to automatically assign tasks, projects, leads, or anything else in Podio to your team members in a round robin fashion.

**Don't want to build the apps and flow yourself? [Contact us](https://forms.momentumtools.io/?form=lqjomvmsqiir&services-requested=5&what-would-you-like-to-purchase%5b1%5d=true) to purchase the app and flow for $200**

To set this up, first you will need to create an app that lists your team members.

**Team Members app fields**

**Name: **Single line text field for employee names

**Status:** Category field with options for Active and Inactive

**Date Last Assigned:** Date field with start date and time

**Podio Profile: **Member field to link the employee's Podio profile

**Role (optional): **Category field for different job roles. This is only necessary if you will have more than one team with round robin assignments.

You can add any other fields you like to this app, such as email address and phone number to store your team's contact information.

**Create a Podio View**

Navigate to your Team Members app, and sort items by "Date Last Assigned, oldest first". Add a filter to show only employees listed as "Active" so that Inactive employees are excluded from the round robin. If you added a Role field, then you should also filter to show only the employees who should be included in this round robin.

Then, click "Save as" and save a new Team view.

![Screenshot](/images/example_round_robin_view.png)

**The Podio Workflow Automation flow**

Next, you will need a flow to manage the round robin assignments. The flow will live in the app where items should be assigned (Projects, Leads etc.), and will trigger on item create. The flow will look as pictured:

![Screenshot](/images/example_round_robin_flow.png)

**Important notes:**

- Be sure your "Get Podio View" action is only collecting 1 item via the "Limit" section

- The "Date Last Assigned" should fill in "Current Date & Time," not just the "Current Date"

**Using the Flow**

With this app and flow, all new items created in your app will automatically trigger the round robin assignment.

If a team member goes on vacation and needs to be excluded from the round robin temporarily, you can simply navigate to their Team Member item and change their Status to "Inactive". Switch them back to "Active" when they return, and they will be first in line to receive a new assignment.

**Questions? [Get in touch](https://zooli.io/contact.html), we are happy to assist!**
