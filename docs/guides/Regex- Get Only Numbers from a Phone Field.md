The following regular expression will return only numerical values from the field token used. This will work with any field type, not just a phone field.

```php
preg_replace("/[^\d]/", "", Phone-Field)
```

**How to use:**

Use a "Create a Custom Variable" action in Podio Workflow Automation, and insert the above expression. Use the token selector to replace `Phone-Field` with the field you would like to use.
