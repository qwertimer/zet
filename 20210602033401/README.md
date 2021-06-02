# Learning Bash - Part 2

This is mainly from Day 17 of the Boosts. - 

NOTE: Always use "" around your passing variables ... This stops nefarious code being run ?? -- check this.

* `>/dev/null` -- is used when you dont want to see the output. It sends output to dev null. 
* `>/dev/null 2>&1` -- sends the stderr to dev null
* In bash you can use `&>/dev/null` which is the same as the above command.

One of robs great scripts is https://github.com/rwxrob/dot/blob/main/scripts/newx. This script creates a file, adds it to the scripts folder and adds to path. Then opens in vim.

Try not to use else in any code. Place a return to return early.


- `test` is a language built in that returns true or false. --- there are many additional switches that are useful.
check more `man test`
- `elf` is a compiled shell script.

 
- Really interesting thing is if you are checking for a file rather than outputting to stdout and possibly messing up logs. send it to stderr and it will still print to screen.
 
example:
``if test $# -ne 1; then
     echo "usage: has <path>" >&2
     exit 1
fi``

 
Note: robs cmt command is able to cmt specific lines using -- `ctrl [` to go to normal mode, then `!{` sets to run a command. Then he writes `cmt`. I need to learn how to select the write length of commenting.

- for loops are great in the command line.
