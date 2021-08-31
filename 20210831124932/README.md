# If you ever need resources on how to exit python programs this is it

Reading through David Beazleys article on exiting python with `raise
SystemExit(0)` i found some excellent gems the article in question is
[SystemExit](https://www.usenix.org/system/files/login/articles/login_winter17_12_beazley.pdf).
Not only does David talk about using -i to keep an interpreter alive.
(see previous post) but he also gives a nice overview of how to write a
context manager to use with a with statement. This is done simply with
the methods `__enter__` and `__exit__`. 
