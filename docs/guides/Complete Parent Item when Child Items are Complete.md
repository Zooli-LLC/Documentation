This guide will show you how you can complete a Parent item when all of its related Child items are marked as complete. In this example, we will use a Project app as the Parent, and a Deliverables app as the Child.

**Need assistance building this flow? [Contact us](https://zooli.io/contact.html), we are happy to help!**

This Podio Workflow Automation flow will be triggered from the Deliverables app on Item Update. Specifically, it will trigger when a Deliverable is set to "Complete".

**The steps of this flow are as follows:**

- **Custom Variable:** "flag" - Set to 0

- **Get Referenced Items:**

    - Forward to Projects via "Related Project"

    - Follow to another app, reverse to "Deliverables" via "Related Project"

- **For Each: **For each "(Ref) Deliverable"

- **Sanity Check: **If [(Ref Deliverable) Status] != "Complete"

- **Custom Variable:** "flag" - Set to 1

- **End If**

- **Continue (end For Each)**

- **Sanity Check:** If [(Variable) flag] == 0

- **Update Collected:** Update Projects - Status to "Complete"

- **End If**

![Screenshot](/images/example_complete_parent_item.png)