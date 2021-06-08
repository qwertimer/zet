# Parameter Expansion

Often times we want to capture certain parts of a variable. For instance when we call $PWD we may only want the current folder or the parents. Using parameter expansion we are able to get a part of the variable. This is instead of creating a subshell when calling a built in program such as basename. To complete parameter expansion and remove certain parts we can use many different keys.

For example if we have the path of a file such as 
`path="/usr/bin/bash";`
If we  wish to remove all infomation up to and including the final /.
The command to do this is `${path##*/}` The result is `bash`. There is a lot more that parameter expansion can do. To learn more `man dash`. /Parameter expansion. Using this we can bypass using `AWK` or `SED`

