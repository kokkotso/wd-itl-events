# Iterable custom events JSON reference
**created for Walker & Dunlop Digital Marketing team**

This repo contains references for Iterable custom event data schema in JSON. These are primarily used in constructing the Zapier zaps to push Webflow form data into Iterable. 

## Usage
In Zapier, copy reference JSON directly into the Iterable App > Configure > "JSON data fields". Make sure you're using the correct reference for the desired custom event (e.g. submitForm, registerWebcast, attendEvent, etc.). Where you see the `((datatype_description))` pattern, replace with Zapier variables representing Webflow form data. All fields are optional.

**Important: For all data types except boolean & number, make sure the variable is encapsulated in quotation marks.**

### Example
`{
  "metadata": {
      "name": "((string_form name or id))"
  }
}`

will look like this in Zapier:

![zapier-variable-example](https://github.com/user-attachments/assets/9423c6f9-e0a4-4e9d-b8d0-2b618007254f)

Some values are hard-coded (rather than relying on variables) - these are usually indicated by `"datatype_option 1|option 2|option 3|"` *without* double parantheses. For these, select the appropriate value for the specific form from the list.

### Example
`{
  "category": ["aff", "app", "brand", "cm", "hud", "mff", "sbl", "senior", "student", "wdip", "wdis", "webcast", "zel"]
}`

will look like this in Zapier:

![zapier-hardcoded-array](https://github.com/user-attachments/assets/61393b43-4b4b-4bf7-8487-ccc89122dc4a)

## Tips
Invalid JSON will fail to pass Zapier tests. Common reasons for failure include:

- You have a trailing comma(s). Properties (key-value pairs) must be separated by commas, except for the last item within an object.
- You have a missing quotation mark(s). Keys (and most values except numbers and booleans) must be encapsulated in **double quotes** - note, this is different from Javascript where double and single quotes are interchangable.

If you're running into issues, try copying your code from Zapier and dumping it into a JSON linter like (https://jsonlint.com/) - it will highlight errors.

For more information on JSON syntax, go to (https://www.w3schools.com/js/js_json_syntax.asp)
