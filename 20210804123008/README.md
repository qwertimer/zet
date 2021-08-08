# Using read correctly in bash

read is a powerful tool in bash. It will read from stdin if you don't
provide anything to the call. To read from something else we can use `<
<file>` which will be read into the variable in the while loop.

example:
```
while read -r line; do
done < /etc/resolv.conf
```

The `-r` makes sure it doesn't read `\`` as an escape character which is
useful when reading files.

