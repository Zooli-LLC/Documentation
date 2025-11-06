Setting up flows to handle duplicate entries in your Podio apps is an important step to ensuring your data is accurate and organized.

The first step is to determine which field in your app to use as the duplicate checker. This can be tricky, as you need to ensure that all values in this field are using the same format. For example, using an address field may not be a good idea as there are several different ways you might enter the same address (i.e. "1234 Main Street, 1234 Main st." etc.)

One option is to use a **Phone** field, and have a separate flow in your app that automatically formats all numbers in the exact same format. See our article on [formatting phone numbers](https://docs.zooli.io/hc/en-us/articles/360035874553-Regex-Get-only-numbers-from-a-Phone-Field) for assistance with this.

Once you know which field you are using in your duplicate search, you are ready to create a new flow in Podio Workflow Automation. We recommend creating a flow that triggers on **Item Create**.

Add a **Search** block to your flow, and have it search your app for a matching value in your duplicate checking field. Be sure to check the "Ignore Self" box, otherwise the search will find itself each time and all new items would be processed as duplicates.

![Screenshot](/images/example_duplicate_search.png)

Next, check to see if a duplicate item was found. Run a **Sanity Check** and see if there is a Podio Item ID for a matching Contact. If so, we update that item with any new details, then delete the duplicate.

![Screenshot](/images/example_duplicate_collect.png)

**Note:** To combine the value of an existing item with the value of the duplicate, insert both field tokens separated by a new line:

```php
[Ref Item](Field) . "\n" . [Item](Field)
```

This will keep the existing values and place the new details right below.

Once you've saved your flow, we highly recommend running a few tests to be sure it is working properly. This is an important step, especially when your flow has the potential to delete items.

**Questions? [Get in touch](https://zooli.io/contact.html), we are happy to assist!**
