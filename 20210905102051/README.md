# Why use the `@property`


The `@property` is a decorator that turns a function into an attribute
of a class. 

The use of the property decorator can be seen below. The issue seen
without the `@property` shows that whilst self.x and self.y change when
moving however the `repr` of the class doesn't update. To fix this one
could add an update function however this is then required to be added
to all of the functions.
*Sample Code*

```python
Class Location:
    def __init__(self, x=0, y=0)
        self.x = x
        self.y = y
        self.loc = [self.x, self.y]
    def move_left(self):
        self.x -= 1
    def move_right(self):
        self.x += 1
    def move_down(self):
        self.y -= 1
    def move_up(self):
        self.y += 1
    def __repr__(self):
        return f'{type(self).__name__}(x={self.x}, y={self.y})'

```
To fix this issue we can add the `@property` to a `loc` method. This is
seen here.

```python
@property
def loc(self):
    return [self.x, self.y]
```
The resulting function can then be called as an attribute with `loc.loc`
where `loc` is the name of the class instance. 

We can create our own property class as seen:

```python
class MyProperty:
    def __init__(self, func):
        self._func = func
    def __get__(self, inst, owner=None):
        return self._func(inst)
```

Property decorators also have functionality such as the setters and
deleters.

These are applied to the function you decorate with the property
decorator. This is done with:
```python
@loc.setter
def loc(self, loc):
    self.x, self.y = loc
```
Which can be called with `loc.loc = [1000, 50]` for example.
The deleter is seen below:
```
@loc.deleter
def loc(self):
    self.x = self.y = 0
```

In python 3.8 in the functools library we have a cached_property
decorator.
This function only gets the value once and stores it for
later, `@cached_property`.



    #python #decorators #@property

