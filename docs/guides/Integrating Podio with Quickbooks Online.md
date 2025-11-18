Quickbooks Online offers a flexible API that allows you to send an receive several different data points with Podio. This guide will walk through the authentication setup, and will create a basic flow that creates Quickbooks Online Invoices from Podio app items. Since there are many different setup requirements depending on your team's needs, this guide can be used as a framework for creating other items in Quickbooks Online, such as Bills, Payments, and more.

This is a developer-level tutorial. Some programming experience is required for this setup.

**We provide a fully set up workspace with Podio Workflow Automation flows for a one-time fee, which includes:**

- Creating Invoices (with Line Item support)
- Creating Bills (with Line Item support)
- One-way integration (Podio to Quickbooks) for Products/Services, Vendors, and Customers

We also offer pay-as-you-go customization. If you are interested in either of the above, please [**get in touch**](https://zooli.io/contact.html) and we are happy to help.

**Watch the video demo:**

**Sending data from Podio to Quickbooks Online**

**For this guide, you will need:**

- **Podio Workflow Automation** (included in all Podio Premium plans)
- [**ProcFu**](http://procfu.com/): Advanced scripting tool built by the original creator of Podio Workflow Automation, formerly known as GlobiFlow (we recommend at least a Bronze plan)
- **[Intuit Developer account](https://developer.intuit.com/app/developer/homepage)** Sign in with your Quickbooks Online credentials

**Step 1: Set up your Podio apps**

The first step is to get your Podio apps set up to contain all the information necessary to send to Quickbooks. We highly recommend keeping entirely separate apps specifically for your Quickbooks data vs. building the integration into apps you are already using for another purpose. This keeps data properly segregated for this purpose and also gives you the option to feed information from multiple workspaces into your Quickbooks apps. 

For creating Quickbooks Invoices, you will need 2 apps: **Customers** and **Invoices**, with an optional third **Line Items** app. 

**Customers App**

The Customers app needs at minimum 2 fields: Customer Name and Customer ID. The Customer ID is the Quickbooks ID for the customer. If you have existing customer in your Quickbooks Online account, you can export that list to Excel and then import it into this app.

**Invoices App**

The Invoices app also needs at minimum 2 fields: A Relationship field to the Customers app, and Invoice Amount. If your invoices will have custom line items (i.e. if the invoices won't always have the same singular line item), then you will also need a Relationship field to a Line Items app, explained below.

**Line Items App (optional)**

The Line Items app needs 2 fields: Line Item Name and Quickbooks ID. These are classified as Items in Quickbooks and can be found in the Products and Services section in your account. Similar to Customers, if you have existing items in Quickbooks Online then you can export that list an import them into this app.

**Step 2: Create an app from your Intuit Developer account**

Log in to your [Intuit Developer Account](https://developer.intuit.com/app/developer/homepage) and select "My Apps" at the top. Follow the steps to create an app for Quickbooks Online and Payments. You can name the app whatever you like, and select Accounting for the scope. 

Once the app is created, navigate to the "Keys & OAuth" section under Production. You may also start by developing in the Development environment if this is your first time setting up this integration. 

In the Production environment, you will see that you need to complete some additional setup information. Once this is done, you will see the Keys & OAuth information for your new app which is used in the next step. 

In the Redirect URIs section, select "Add URI" and add [https://procfu.com/authenticate.php](https://procfu.com/authenticate.php).

**Step 3: Set up API Configuration in ProcFu**

ProcFu is what will allow Podio to communicate with Quickbooks Online's developer API. To begin this setup, log in to ProcFu and go to Menu -> Configuration. In the upper right, click the "[Add API](https://procfu.com/apiService.php?id=0)" link. Fill out the next page with the following:

- **Service Name:** Your choice. We usually use "quickbooks_production"

- **Client ID: **Client ID from your app created in Step 1

- **Client Secret: **Client Secret from your app created in Step 1

- **Authorize URL:** [https://appcenter.intuit.com/connect/oauth2](https://appcenter.intuit.com/connect/oauth2)

- **Scopes: **com.intuit.quickbooks.accounting

- **Access Token URL:** [https://oauth.platform.intuit.com/oauth2/v1/tokens/bearer](https://oauth.platform.intuit.com/oauth2/v1/tokens/bearer)

- **Resource Owner Details URL:** [https://accounts.platform.intuit.com/v1/openid_connect/userinfo](https://accounts.platform.intuit.com/v1/openid_connect/userinfo)

- **Redirect Success URL:** Your choice. We usually use the Podio workspace URL.

- **Redirect Failure URL:** Same as above

**Step 4: Building your Podio Workflow Automation flows**

**Authenticating for the first time**

You will need to set up a flow using the [[API Get Login Link ProcFu script]{.underline}](http://procfu.com/script.php?s=api_get_login_link.pf). The API Service parameter is the Service Name from Step 3 and the User ID is the email address for your ProcFu account. The response for this call is an OAuth login link - we recommend setting up a Task as part of this flow containing the login link, then run the flow once to receive the link.

**Creating Customers**

This flow will live in your Customers app. We recommend setting this as a Manual flow so that you can set up multiple triggers to create customers. Create a custom variable which contains the payload to be sent to Quickbooks. A simple example payload:

```php
foo();function foo(){
    return json_encode([
        "DisplayName" => {Contact Name},
        "PrimaryEmailAddr" => [
            "Address" => {Contact Email}
        ]
    ]);
}
```

Send this payload using [ProcFu's Make API Request script](http://procfu.com/script.php?s=api_make_request.pf). The URL for this particular call is:

[https://quickbooks.api.intuit.com/v3/company/{CompanyID}/customer](https://quickbooks.api.intuit.com/v3/company/%7BCompanyID%7D/customer)

Extract the Customer ID from the response and store it in the Customer ID field in your app. The variable we used for this is:

```php
json_decode([(Variable) create_customer_response], true)["Customer"]["Id"]
```

 **Creating Invoices**

This flow lives in the Invoices app. Similar to Customers, we recommend setting this up as a Manual flow so that you can have multiple triggers as needed. This flow also sends a payload via ProcFu's Make API Request script. Follow [Quickbooks Online's Create Customer documentation](https://developer.intuit.com/app/developer/qbo/docs/api/accounting/most-commonly-used/customer#create-a-customer) to format your request. Here is an example payload:

```php
foo();function foo(){
    return json_encode([
        "Line" => [
        [
            "DetailType" => "SalesItemLineDetail",
            "Amount" => {Amount},
            "SalesItemLineDetail" => [
                "ItemRef" => [
                    "name" => {Line Item Name},
                    "value" => {Line Item ID}
                    ]
                ]
            ]
        ],
        "CustomerRef" => [
            "value" => {Quickbooks Customer ID}
        ],
        "CustomerMemo" => [
            "value" => {Memo}
        ],
        "AllowOnlineACHPayment" => true,
        "BillEmail" => [
            "Address" => {Customer Email Address}
        ],
        "SalesTermRef" => [
            "value" => {Sales Terms}
        ],
        "TxnDate" => {Invoice Date},
        "DueDate" => {Invoice Due Date}
    ]);
}
```

Be sure to thoroughly test these flows prior to using them with your customers. And as always, if you have any questions, do not hesitate to [get in touch](https://zooli.io/contact.html) and we will be happy to assist. 
