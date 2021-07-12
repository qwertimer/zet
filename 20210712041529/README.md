# Expand multiple array strings with "{A[@]}"

We can expand arrays in bash using multiple different methods. If we
want to get all the string as one we can use the `${A[*]}` to split by
word.
To get all the values of the array in one line. We can use `"${A[*]}"`.
We can do `"${A[@]}"` to split by chucks.

For example we have :

A = ["this is a string,", "and another one,", "last"]
- ${A[*]} = This, is, a, string, and, another, one, last
- "${A[*]}" = "this is a string, and another one, last"
- "${A[@]}" = this is a string
               and another one
               last



