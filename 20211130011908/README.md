# Incorporating fastcore into everday python work

Whist fastcore is designed for use with the fastai library for deep learning there are some very useful tools for use in normal development frameworks. Some of these i have outlined below.

* Setting instance attributes
  Rather than having to write:
```python
  class Test:
    def __init__(self, a, b ,c):
        self.a, self.b, self.c = a, b, c
```
  the library provides a helper function. `store_attr()` which reduces code duplication. We can also use a keyword `but` to exclude any attribute.

* Type Dispatch
  Or multiple dispatch allows 'function overloading' where by the function dispatches to different methods based on the type passed. The only issue in this regards is the requirement to type annotate your code.
  To implement this we can use the `@typedispatch`

* basic_repr
  Functionality to add a simple repr based on the attributions in the `__init__`.

* patch and patch_to
 
  Decorator functions to monkey patch classes using type annotations. You can use `as_prop` and `cls_method` with the decorator. `as_prop` allows the method to act as an attribute. The `cls_method` will add the `classmethod` decorator to the function.

* fast scripting tools
  
  fastcore.script provides wrappers around argparse to make cli tooling fast. just decorate your function with `@call_parse`, provide type annotation followed by a comment and the program will autoscript with help and the prewriiten switches.
```python
from fastcore.script import *
@call_parse
def main(msg:str,     # The message
         upper:bool): # Convert to uppercase?
    "Print `msg`, optionally converting to uppercase"
    print(msg.upper() if upper else msg)
```


