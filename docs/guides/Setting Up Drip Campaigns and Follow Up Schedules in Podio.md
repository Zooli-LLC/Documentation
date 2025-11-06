Setting up drip campaigns is an excellent way to to automate communication with your leads, and can eliminate hours of manual entry for you and your team. This guide will walk you through building the apps and flows for a successful drip campaign or follow up schedule.

**Need assistance setting up? [[Contact us]{.underline}](https://forms.momentumtools.io/?form=lqjomvmsqiir&services-requested=5&what-would-you-like-to-purchase%5b5%5d=true) to purchase these apps and flows for \$600.**

**Follow Up Schedule App**

The first step is to build your Follow Up Schedule app in Podio. This app will act as the instruction list for your follow ups. This will be structured in a way that allows you to store multiple campaigns or schedules, and you can also set multiple follow up types (**Email** and **SMS** are included here - **Ringless Voicemail** via SlyBroadcast is also an option but requires some additional setup).

The Follow Up Schedule App requires the following fields:

- **Title:** Calculation field combining **Schedule** and **Sequence** below. Note you will need to save your app with the below fields before you can add this field.\
  ![A screenshot of a computer
  AI-generated content may be incorrect.](media/image1.png){width="6.5in" height="1.1347222222222222in"}

- **Schedule: **Category field with options for each different schedule you would like to include

- **Sequence: **Number field noting the order of each follow up in the schedule

- **\# Days to Go Out: **Number field noting how many days the follow up should go out after the follow up schedule starts

- **Email Subject**: Text (Single Line) for the email subject

- **SMS or Email Body**: Text (Multi Line) for the body of the SMS or email

Add an item to this app for each instance of your follow up schedules. Make sure your \"# Days to Go Out\" is always increasing with each number in the sequence, otherwise your flow will eventually get stuck as a follow up would be scheduled in the past.

**Prepping your Podio App**

Next, you will need to add a few fields to the Podio app that contains your contacts for these follow ups. This could be your Leads or Contacts app, or any other app that stores this type of information.

Consider adding a [[section header]{.underline}](https://docs.zooli.io/hc/en-us/articles/360035864973-Podio-Calculation-Creating-a-section-header) to this area in your app to visually separate these fields from the rest of your app.

Your app will need the following fields:

- **Follow Up Schedule:** Category field with options for each schedule, matching the schedules in your Follow Up Schedule app. This field is used to activate the selected schedule.

- **Follow Up Start Date**: Date field (autofilled via Podio Workflow Automation)

- **Next Follow Up Date: **Date field (autofilled via Podio Workflow Automation)

- **Next Follow Up:** Relationship field pointing to the Follow Up Schedule app (autofilled via Podio Workflow Automation)

**Building the Flows**

Now you are ready to set up your automations.

**Flow 1: Starting the Schedule**

The first flow will trigger when your \"Follow Up Schedule\" field is updated on a lead. This will begin your follow up Schedule.

The flow will need to locate the first sequence in the selected follow up schedule. Build a search_string variable and set it to \"{sequence_name} . \" \" . 1\"

![](media/image2.png){width="6.5in" height="0.6951388888888889in"}

Next, add a Search action and search your Follow Up Schedules app for an item whose Title matches your search_string variable. If a matching item is found, update your current item with the information on the located follow up. You will fill in the **Follow Up Start Date**, **Next Follow Up Date** (adding the \# Days to Go Out field to the current date), and the **Next Follow Up** item.

![A screenshot of a computer
AI-generated content may be incorrect.](media/image3.png){width="6.5in" height="2.3465277777777778in"}

**Performing the Follow Up Actions**

Now that your follow ups are scheduled, it\'s time to build flows to send out your follow ups on the scheduled dates. This flow will trigger \"By an Item\'s Date Field\", when **Next Follow Up Date** is equal to the current date. Be sure to adjust the trigger time to a reasonable time in your time zone, so that you aren\'t messaging your contacts in the middle of the night.

The first step in the flow will be a **Get Referenced Items** action that gets the Follow Up item via the \"Next Follow Up\" field.

You will need two sections to this flow - one for follow ups that are of type \"SMS,\" and another for follow ups that are of type \"Email\". Use Sanity Checks for each of these sections.

For **Email** follow ups, perform a Send Email action, filling in the Email with the Email Subject and Body from your Follow Up Schedule app.

**Note:** If your contact\'s email address is an **Email** field type, you will need to parse out the email address using the variable shown below.

![A screenshot of a computer
AI-generated content may be incorrect.](media/image4.png){width="6.5in" height="7.0625in"}

For **SMS **follow ups, use a \"Send SMS\" action, filling in the body with the SMS Body from your Follow Up Schedule app.

**Note:** Your \"To\" number must be in format \"+1xxxxxxxxxx\" in order to be sent. See our article on [[formatting phone numbers]{.underline}](https://docs.zooli.io/hc/en-us/articles/360035874553-Regex-Get-only-numbers-from-a-Phone-Field) for assistance with this.

Once the follow up has been sent, the next follow up will need to be scheduled. To do this, we will need to find the next follow up in our sequence. Create a new sequence variable and set it to the current follow up sequence + 1, then create a search_string variable, setting it to your Schedule Name + Sequence.

![A screenshot of a computer program
AI-generated content may be incorrect.](media/image5.png){width="6.5in" height="1.2756944444444445in"}

Now do a \"Clear Collected\" items action to forget your current Follow Up, and run a new Search for your Follow Up Schedule app that looks for your new search_string.

Lastly, perform an update item on your current item, updating the **Next Follow Up **and **Next Follow Up Date **based on the located schedule item.

That\'s it! This is a bare bones follow up sequence flow, but there are many other possibilities you can add in to automate even more. Some suggestions:

- Add error handling comments to let you know if something has gone wrong

- Add a \"Pause\" button with associated flows to pause or stop the schedule

- Add flows to auto-stop a sequence if the contact replies to your SMS or Email.

**Questions? [[Get in touch]{.underline}](https://zooli.io/contact.html), we are happy to assist!**
