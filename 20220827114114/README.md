# Using !! on cli with string replacements

Often times i am running a command that either i need to modify or i
have made a mistake and want to rerun. To fix this i can either go back
up in the history and modify the command or i can use a useful trick of
adding substitution or replacement with the !! and
`:s/<item>/<replacement>` command.

For example i can change systemctl start to status with
`!!:s/start/status` and i can rerun with status instead of start whilst
it isn't as easy as tapping up and using the arrow key it is probably a
nicer way to change things.


