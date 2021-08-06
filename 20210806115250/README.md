# tmux session basics

We can create new sessions with `tmux new-session`. We can also switch
sessions from inside tmux using. `Prefix (` to attach to previous
session. `Prefix )` to attach to next session. `Prefix L` to attach to
last session and `Prefix s` to select a new session for the attached
client. `Prefix s` is similar to `Prefix w` to look at windows.

To name a session we can use `Prefix $`. We can also rename from the
command line with `tmux rename-session -t 1 "my session"`



