# `printf` and its abilities in bash

`printf` has some excellent features to expand on your output
capabilities. The `printf` function has the ability to print out the
date with the command `printf '%(%F)T'` which will output the current
date. 

We can also use the `-v` flag to output to a variable. Where the first
value is the variable name. Whilst the second value is the input into
the variable. This is similar to `sprintf`.

`printf '%s\n' "$Data"` places the second value in place of the `%s`
similar to many other languages. `s` can be replaced by other values
such as `d` for number.

We can also use `%'d` to output the decimal value with a comma.
