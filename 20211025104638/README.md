# Mental Note for running jupyter lab

Run jupyter lab with `jupyter lab 2>/dev/null &` to clear output and free up the terminal. This is helpful when not
running tmux and not wanting to open another terminal. To kill the jupyter lab we can run `kill -9 $(ps aux | grep
[j]upyter | awk '{print $2}')` which basically runs the process search with<Plug>PeepOpens, greps for jupyter without
grepping for the grep process, this is done with the [j]. Then the awk statement is used to show the process that is
killed. Finally this is all wrapped in a process substitution which is then sent to the kill command with a sigterm `-9`

For fun i wrapped it in a program to kill jupyter and other programs if needed. The script is below.

```bash
#!/bin/sh

# Description: Simple program to kill a specific process from the command line. This uses ps, grep, awk and substring
# searching. Not the most elegent way to kill a program.

file=$1
first=${file:0:1}       #get first letter
grepfirst=["$first"]   #used to remove grep command from ps
last=${file#$first*}    ## alternative  last=$(cut -d $first -f2 <<< $file) #get everythin after the first letter
res=$grepfirst$last
echo "$res"
kill -9 $(ps u | grep $res | awk '{print $2}')
```
