---
title: Elements
layout: home
nav_order: 3
---
# Elements
This section includes details on elements, we've divided them into Locators and Templates:
- `Locator`
- `Template`

### Locator
A locator is a single xpath, css selector, or JS query linked to a template. This locator can match to multiple fields, each of which are intended to be of the same type. e.g. a locator might point to 12 rows under the same column.
This class consist of the following methods:

- find()
  - This method uses the xpath from the provided template to find the elements. If the template has the 'optional' tag then it will find this instead.
- is_visible()
  - Argument: element
  - Takes the non-stale element and verifies if it's visible. 
  - Returns: Visability as a boolean.
- find_options()
  - If the provided template has the 'options' parameter this script will run and replace all discovered elements.
  - In FinOps we identify the column and then use the template option to traverse to the actual rows. 

### Template
A template is a single xpath, css selector, or JS query that identifies a field type. This also uses the '${name}' variable to find a specific locator of that field type.
For example, a page might have 10 fields of type dropdown, and we only want the locator for the 'address dropdown'.

- strip_index()
  - Removes the index from the field name
- strip_postfix_index()
  - Removes the index from the field's postifx.
- refresh_templates()
  - re-loads the templates json file
- exact_match()
  - Some templates enforce an exact field name to be used. E.g. "Warning Message" and don't allow the dynamic field name variable: '${name}'
  - This method returns all of these cases.
- post_match()
  - This method will return all paths (xpath, js, etc) where the field name contains the templates postfix value.
- generic_match()
  - Returns all paths (xpath, js, etc) for templates without post/prefix or exact match.
  - Commonly used for standard fields, e.g. input fields where we locate the element using only the input's label.
- apply_mutators()
  - Applies mutators to the xpath. 
  - Mutators can be specified on a template.json level, although, put simply it's used for things like xpath lower-case and normalize-space.
- get_option()
  - Returns the templates option value if applicable. 

