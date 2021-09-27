# subclasses in python for creating overloaded classes

Watching mcoding [__new__ vs
__init__](https://www.youtube.com/watch?v=-zsV0_QrfTw) he showed a
useful setup for creating a single class overlaying multiple underlying
subclasses to process varying input types. The main function called.
EncryptedFile().read() which contained a plain text, rot13 and otp files
to read in.

For each of these file types a class is created with a read method. The
classes each run varying decryption functionality. The main idea is
having the class contain the EncryptedFile parent class. 

The main EncryptedFile class contains a `_registry = {}` which maps the
prefixs to classes. The registry is populated by using an
`__init_subclass__` hook.

```
def __init_subclass__(cls, prefix, **kwargs):
    super().__init_subclass__(**kwargs)
    cls._registry[prefix] = cls
```

The prefix and subclass are stored in the reqistry. Then when the
`__new__` method is called at class creation the code calls the below
`__new__` method.

```
def __new__(cls, path, key=None):
    prefix, sep, suffix = path.partition(:///')  ##specific to the setup
    of the video.
    if sep:
        file = suffix
    else:
        file = prefix
        prefix = "file"
    subclass = cls._registry[prefix]
    obj = object.__new__(subclass)
    obj.file = file
    obj.key = key
    return obj
    
```

The prefix is pulled out of the registry and stored in the subclass.
Then the subclass is initialised with the `__new__` command. 

This design could be incredibly useful when loading in data from
different datasets for deep learning and other projects.
