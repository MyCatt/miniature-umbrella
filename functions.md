---
title: Functions
layout: home
nav_order: 2
---
# Functions
Functions are scripts that take an element and interact with it in a specific way. Examples of functions are:
- `enter values`
- `click`
- `get value`

There are two types of functions, native and custom. Both of these can be found in `functions.py` which has them split with comment blocks. Ensure that any new functions are added after the custom functions comment block.

```
'''
    Title: Custom Functions
    Description: Use this for adding/updating custom functions, less likely to break tests by changing these.
'''
```

### Native
Native functions concists of `enter_values`, `click`, and `get_value`. These are designed to handle the most basic element interactions and will be the fallback for custom functions. 
Native functions should work with all vanilla html elements, supporting Chrome, Firefox, and Safari.

### Custom
Custom functions, as the name implies, should be used when a native function is unable to correctly interact with an element. These custom functions can be specified through `templates.json` in the following format:
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

From `template.json` you can assign a custom function to any native function. These custom functions will be called in the order that they appear, starting at index `0`. If the function at index `x` fails, then the next specified custom function, index `x + 1` will be executed. If all of these fail the framework will run the native function as a fallback.

## Arguments
Each function requires the following mandatory arguments:
- `framework`
- `field`

`enter_values` will also require a `value` to be provided


#### Framework    
This is the framework object and contains a reference to the driver. Framework objects are instantiated at the begginning of a test.
- `framework = Framework('name of test')`

#### Field
This is the field the function will use to try and locate the element.

#### Value
`enter_values` also requires a value arugment in order to know what data to pass into the discovered field.

### Additional Arguments
#### Iteration
You might also notice that all functions have an iteration argument, defaulting to 1. This is non-mandatory and is used by the test to control the amount of times it will attempt to perform the function. By default this is 5 times. 


You can force a function to only run once by passing the value `4` in this argument.
