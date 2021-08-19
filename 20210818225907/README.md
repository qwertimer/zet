# bash variable expansions

Here are some notes on variable expansions from the Youtuber nixcasts.

* We always want to wrap variable results in quotes as without it new
lines and other things wont get expanded. Bash separates fields based on
the internal field separator which is `IFS`.
*  Arrays should be wrapped in `()` otherwise for example if we define
   an array with `*` for example in a directory with `a.txt b.txt c.txt`
   we actually expand to `* b.txt c.txt` which is incorrect. When we
   call the array we use `"${files[0]}"` where files is given as
   `files=(*)`
* We wrap variables in `{}` to be able to add other extensions to be
  added. For example we can add an s to the variable by having
  `"{file}s"` which will expand the `file` variable and add the s at the
  end. If this wasn't done we would end up with a different variable
  that it is trying to expand.
* We can use the `{}` to allow us to slice the variable. For example we
  can use a variable such as `test="check it"` and call the variable with
  `"${test:0:5}"` which will only output `check`, this syntax is start
  at value 0 and output the next 5 characters. This is also seen with
  `"${test:6:2}"` which will show `it`
* The `:` will allow us to get certain elements of an array as well. We
  can have an array called `files` and `"${files[@]:3:6}"` will output 6
  array values starting at array number 3. Bash is 0 start so it will
  start with the 4th value in the array.
* `#` the hash sign at the start of the array will output the size of
  the array. `"${#files[@]}"`. This also works to output length of
  variable.
* `%` will remove the value shown after the symbol. For example with the
  test variable above if we do `"${test% it}"`, the output will just
  show `check`. Percent works with the suffix.
* Using the `#` after the variable name will remove the prefix listed
  after the symbol. For example with test we can remove check with
  `"${files#check }"` where the trailing whitespace is part of the
  removal.
* The difference between `%` and `%%` is the `%` will remove the first
  match of the value following the `%`. eg. `"${test%c*}"` will result
  in `che`, remembering that the `%` matches from the end back. While
  `%%` will remove the last match that it finds. Which in this situation
  will be starting at the first letter and therefore there will be no
  values left. It is important to note that the `*` is matching any
  character. If we didn't have the `*` it wouldn't match and remove
  anything.
* We can upper case parts of the variable with numerous modifiers. The
  first `^` will upper case the first letter, if we do `^^` it will
  upper case all letters and if the value is followed by a character that
  letter will be upper cased through out the variable. If we use the `^`
  followed by a letter it will upper case the first instance of that
  letter. Alternatively we can do the `,` in the same way and it will
  lowercase the letters. we can swap cases using the `~` symbol, and all
  symbols with `~~`.
* If we want to do in place replacement of a variable rather than piping
  to sed we can do it directly in bash for example we can change our
  test variable with `"${test/hec/hoc}"`
* Similarly to sed if we want to find all occureances like in sed with
  the `/g` flag we can use `//` at the start. So to find and replace all
  c's in the test variable we can use `"${test//c/t}"`.
* We can also change the first value found in the line with
  `"${test/#check/black}"` which will change check it to black it.
* All of these can be done on arrays.
* If we wish to check if a variable is defined otherwise output a value.
  We can use the `:-` to output a different value if it is undefined.
  For example we have a variable set by `empty=` this variable is empty.
  We can provide a value or a response with `echo "${empty:-Not here.}"`
  to output that the variable is empty.
* The `:+` does the opposite if the value is undefined use that
  otherwise use the value on the right side of the `:+`. If the value is
  defined use the value on the right side.
* Using the `:?` will exit the script throwing the error written on the
  right side of the `?` if the value is undefined.
* `:=` will assign the value on the right to the variable on the left
  overwriting the current value.

There is a lot available in bash to do fast and cool things and this
resource is incredibly useful. To find out more watch the video [Bash
variable expansion](https://www.youtube.com/watch?v=yTijxqjZhRo)



