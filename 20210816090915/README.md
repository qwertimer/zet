# Working with find and `xargs`

Rather than using ls when scripting it is better to use the `find` command
which will output the files in the current folder if the command is
scripted correctly.
If we use `find -maxdepth 1 -type f -print0` we can get all files in the
folder delimited by a null command. The term `maxdepth` stops recursion.
`type f` will give only files and `print0` outputs the results as null
delimited.
We can then send this into `xargs` using the command `xargs -0 -n1`
which will send the results of `find` one at a time to `xargs`

The whole pipe:
`find -maxdepth 1 -type f -print0 | -xargs -0 -n1 -t`


