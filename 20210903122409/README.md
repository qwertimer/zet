# Using pytest and capsys for checking errors and running tests

**

To begin

capsys.readouterr() can capture out and error then we can use assert out
== 'whatever' and asseer err == ''


We can also send print statements directly to locations for example
sending the string error to sys.stderr will allow you to catch the
errors on the terminal.

We can do this with:
```python
  print("Error message", file=sys.stderr)
```


