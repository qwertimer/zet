# TMUX sessions and configuring startup scripts.

TMUX has some powerful features available for use in the form of startup scripts. These allow the user to configure a shell script to set a tmux session and open panes for each workspace and folder that is needed for that particular project. When used alongside VIM this setup allows docmentation, coding and note taking to be done all in the same terminal session. This design allows the port of a startup script to be added to a remote container or system that is called when remotely logged in.  

The simple configuration can be done with a few commands.

The first command is:
`tmux new-session -s <session-name> -n <new-window-name> -d`
We create a new session and name it using the -s flag. Then we create a new window with the -n flag, finally we detach from it whilst configuring the rest of the init.

Next we can add additional windows/tabs with 
`tmux new-window -t <session-name> -d -n <window-name>`

simply put we add a new window to `<session-name>` detach with the -d flag and name the window what ever we wish with `-n <window-name>`

We are then able to send commands to the windows such as running a python script with:
`tmux send-keys -t <session-name>:<window-name> "python3 hello-world.py"     Enter`
which starts our python script on the `<window-name>` tab.

We are also able to call the splitting of windows if we wish with:
`tmux split-window -h` or `tmux split-window -v`, This however is done after we select which window we are working on with:
`tmux select-window -t <session-name>:<window-name>`

Finally when the script is fully written we add:
`tmux -u attach -t <session-name>`
to start the tmux session.

WARNING: It is important to note that if you rerun the script multiple times it will embed the new windows in the previous session. It will not create a new session. This may cause issues with the running scripts so be careful.
