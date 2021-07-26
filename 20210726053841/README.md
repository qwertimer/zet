# Integrating ? lynx search into vim and tmux

I have been looking at a way to integrate lynx searching into my vim
workflow by having the ability to open a search from normal mode. The
script is seen below. This script checks the current window for whether
or not it is a vim window. ( Careful if you change the window name this
wont completely work). It also checks whether you have an active window
at window 9, if so it will exit the window. It will then create a new
window in the current session at window 9. Then exec lynx and the
search. Once done it checks whether the window that lynx was executed
form was a vim session if so it sends enter to the vim window to fix the
issue with "Press enter to continue" message that vim sends when you
open a new program.


```
#!/bin/sh

val=`tmux lsw -F '#{window_name}#{window_active}'|sed -n 's|^\(.*\)1$|\1|p'`
tmux has-session -t $session:9 2>/dev/null 
if [ $? = 0 ]; then 
    tmux send-keys -t $session:9 "q exit"
fi
tmux new-window -t $session:9

tmux send -t $session:9 "exec lynx \
    'https://lite.duckduckgo.com/lite?kd=-1&kp=-1&q=$*'" Enter
tmux select-window -t $session:9

if [ $val = "vim" ]; then 
    echo "vim is here"
    tmux send-keys -t $session:$val "C-m"
fi
```


