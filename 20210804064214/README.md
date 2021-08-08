# Understanding what !} does

If i have a group of lines that i want to send to a shell script if i
type `!}` it will send the current line and the rest of the lines in a
'paragraph'. ie same level of indentation.

The command converts to ed commands where `.,.+8` `.` is current line
`,` is too `.+8` lines and send to `!(script)`

This allows you to really benefit from the Unix philosophy where you can
pipe inputs and outputs to other commands.
