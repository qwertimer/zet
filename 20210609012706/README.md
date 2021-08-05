# Using vimagics to get cli interface support.

One of the greatest things about vim is the ability to use what some people call vimagics. Some of the functions include: 
`!!` - To get into this mode from in normal mode if we type `shift 11` we start line magic. From here we can send the line to whatever program we want. For instance we can write a python for loop and we can send this to python using `!!python`. 
`%!` - This command will send the whole file to whatever program you want.

We can do so much with vimagics.

`!}` - If we want to send a section to a command we use `!}` which will send the whole section to the next program.

`!13!` - The command will send from the current line to line 13 to the command that will be typed next.

`# For example we sent this line and the following three lines to `cmt` a program that comments the lines.`
`# This is done using !:16.`
`# Line is commented`

It is of note that the `:16` refers to the line the commenting will end before. ie. Up to but not including line number 16. This is incredbly useful when working with python and other programming languages.

 

