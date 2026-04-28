Formatting all phone numbers in your app can be helpful for data visualization, or for enabling phone numbers to be used as a [Duplicate Handling Key](https://docs.zooli.io/guides/Duplicate%20Handling%20in%20Podio/).

Use the following script in a Custom Variable block to format all phone numbers in (xxx) xxx-xxxx format. 

```php
foo(); function foo() {
$type_array = [];
$numbers_array = [];
$result_array = [];
$result = "";
$numbers = explode(",", PHONE-FIELD);
$numbers_amount = 0;
for ($i = 0; $i < 15; $i++) {
$numbers_amount = $numbers[$i] !== null ? $numbers_amount + 1 : $numbers_amount;
}

for ($j = 0; $j < $numbers_amount; $j++) {
$type_array[$j] = explode(":", $numbers[$j])[0];
$this_phone = preg_replace('/\D+/', '', explode(":", $numbers[$j])[1]);
$this_phone = substr($this_phone, 0, 1) == 1 ? substr($this_phone, 1, 10) : $this_phone;
$this_phone = "(" . substr($this_phone, 0, 3) . ") " . substr($this_phone, 3, 3) . "-" . substr($this_phone, 6, 4);
$numbers_array[$j] = $this_phone;

$result_array[$j] = $type_array[$j] . ":" . $this_phone;
}

return implode(",", $result_array);
}
```

**How to use:**

Use a "Create a Custom Variable" action in Podio Workflow Automation, and insert the above expression. Use the token selector to replace `PHONE-FIELD` with the field you would like to use.
