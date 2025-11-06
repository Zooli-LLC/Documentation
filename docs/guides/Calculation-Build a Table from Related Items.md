**Please note that this is an advanced calculation. If you would like some assistance setting this up, please don\'t hesitate to [contact us](https://zooli.io/contact.html).**

The following example creates a table of associated deliverables with 4 columns: Deliverable Name, Status, Owner, and Due Date.

//Pull in the values for each of the columns you want, and set \'numColumns\' equal to the number of columns in your table\
\
var deliverableNames = \@All of Deliverable Name with nulls;\
var dueDates = \@All of Due Date with nulls;\
var owners = \@All of Deliverable Owner with nulls;\
var statuses = \@All of Status with nulls;\
var numColumns = 4\
\
//Set up the table header with the header names, along with a \"\-\--\" for each column (comma separated)\
\
var table = \[\];\
table.push(\[\"Deliverable Name\", \"Status\", \"Owner\", \"Due Date\"\]);\
table.push(\[\"\-\--\", \"\-\--\", \"\-\--\", \"\-\--\"\]);\
\
//Loop over all related items and create a new row in the table for each set of values. Notice the variables defined above are plural, while the ones in this section should be singular\
\
for (var i=0; i \< deliverableNames.length; i++) {\
var deliverableName = deliverableNames\[i\];\
var dueDate = new Date(dueDates\[i\]);\
var owner = owners\[i\];\
var status = statuses\[i\];\
\
\
table.push(\[deliverableName, status, owner, moment(dueDate).format(\'L\')\]);\
\
}\
\
//No adjustments needed in this section\
\
var text = \"\";\
var rows = table.length;\
var columns = numColumns;\
for (var i=0; i\<rows; ++i) {\
text += \"\|\";\
for (var j=0; j\<numColumns; ++j) {\
text += table\[i\]\[j\] + \"\|\";\
}\
text += \"\\n\";\
}\
\
text;

**The resulting table will look like this:**

![A close-up of a list of words
AI-generated content may be incorrect.](media/image1.png){width="6.5in" height="1.1020833333333333in"}

**Notes on this calculation:**

- When pulling in your variables in the first section, be sure to select the option \"with nulls\". Otherwise, your table data will be mismatched if any of your related items have an empty field.

- When pulling in your variables, be sure to select items from the same direction (i.e. don\'t select some \"Incoming\" values and some \"Outgoing\". They should all be one or the other).

- If you have a date field in your column, be sure to define it as \"new Date\" as shown in the for loop section, then use moment(dueDate).format(\'L\') when pushing it to your table to get it in mm/dd/yyyy format. More formatting options can be found [here](https://momentjs.com/docs/).
