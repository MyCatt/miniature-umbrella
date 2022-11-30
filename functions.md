---
title: Functions
layout: home
nav_order: 2
---
# Functions
Functions are scripts that take an element and interact with it in a specific way. Examples of functions are:
- enter values
- click
- get value

There are two types of functions, native and custom. Both of these can be found in `functions.py` which has them split with comment blocks. Ensure that any new functions are added after the custom functions comment block.

```
'''
    Title: Custom Functions
    Description: Use this for adding/updating custom functions, less likely to break tests by changing these.
'''
```

### Native
Native functions concists of enter values, click, and get value. These are designed to be the most basic element interactions and will always be the fallback for all custom functions. 
Native functions should work with all vanilla html elements, supporting Chrome, Firefox, and Safari.

### Custom
Custom functions, as the name implies, should be used when a native function is unable to correctly interact with an element. These custom functions can be specified through templates.json in the following format:
```
        {
          "description": "",
          "xpath":  "",
          "attribute": "",
          "match": "",
          "value": "",
          "mutators": [],
          "function": {"click": ["click_input_link"], "enter": [], "get": []},
          "option": ""
        }
```

From template.json you can assign a custom function to any native function. The functions will be called in order, starting at index 0. If the function at index x fails, then the next specified function, index x + 1 will be executed. If all of these fail the framework will run the native function as a fallback.
