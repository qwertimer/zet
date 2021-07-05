# Imports and packages in python

We can use the `__all__` in a module to define the import * scope. For example if we have a module, a python `.py` file we can define the functions that the import statement can see through using `__all__ = ['foo', 'bar']` to provide access to the foo and bar modules. If we had a different function called apple the import * would not see this function.

`__init__.py` is used to make a directory a python package.
   - init can be an empty file or execute initialisation code for the
     package or set the `__all__` variable.


