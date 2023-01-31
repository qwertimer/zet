# awk foo

There is so much we can do with awk on top of the standard getting of a
certain value with `{ print $3 }`.
For example we can use regular expressions to search for a value inside
the file and only print a column if that line contains the regex. For
example
```
awk '/label/ { print $1 }'
```
will print the first column if the line contains the label. 
We can also send data from a file into awk by placing the file at the
end of the command items to input the file rather than piping it from cat.

Awk also has the ability to write functions. We can do that with the
`func` keyword.

