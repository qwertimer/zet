# Use !$ to expand last parameter of most recent command

When running commands in the terminal we can use `!$` to expand the last parameter, this is useful if you're running a command and then wish to use it in the next line.
An example of this is when we create script then need to `chmod` it.

```
vi coolscript
chmod +x !$
```
Where !$ will expand out to coolscript.

