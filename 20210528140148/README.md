# Working with vim magics.

Vim has an incredible feature built in that rwxrob has coined vimagics. These magics can be accessed using normal mode. To access normal mode we use `esc`, `ctrl [` or `jk` if it is mapped. When in this mode we can use `!!` to send the current line to the program in question ie. `!!bc` will send the current line to the calculator. We can make use of this in many ways like adding the calendar to the current file.

```
      May 2021        
Su Mo Tu We Th Fr Sa  
                   1  
 2  3  4  5  6  7  8  
 9 10 11 12 13 14 15  
16 17 18 19 20 21 22  
23 24 25 26 27 28 29  
30 31                 
```

We can also use it with python, or any other language allowing in line display of file structure or any of these sorts of things.

The biggest draw of vimagics is in the use of the `!}cmt` this comments out the current line. Allowing fast commenting and uncommenting of lines.

To read more on vimagics check out rwx.gg/tools/editors/vi/how/magic/ where Rob gives an excellent overview of vimagics.
