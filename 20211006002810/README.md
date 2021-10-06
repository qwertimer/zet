# Use yad to output a display for script help

yad is a useful tool that i have used to create a script output of my
keybindings for sxhkd. The program takes in the result of an awk or sed
command and displays it in a pretty way. In my helpsxhkd script the awk
program scans for `#` to find the comment on the command and outputs the
command below the comment followed by a tab separated comment.

The script is below.
```
awk '/^[a-z]/ && last {print $0,"\t",last} {last=""} /^#/{last=$0}' ~/.config/sxhkd/*config |
    column -t -s $'\t' |
    yad --text-info --back=#282c34 --fore=#46d9ff --geometry=1200x800 
```

This simple script is then bound to a keybinding in my skhxd config to
be able to show the keybindings set for sxhkd.

