# Command substitution

There are two methods fo commands substitution the old way using
backticks \` or the new method using `$()`. There are times when you
would like to use one over the other. For example using the `$()` is
beneficial when we have multiple nested commands. The use of the
backticks is great for when we want to quickly produce a result for
instance in `\`which FILE\``.

An interesting bit of information seen in the video from
[terminalforlife](https://www.youtube.com/watch?v=qU4maL_smOs) is:
```
Data=`< "$HOME"/.bashrc` 
```
This command will read the contents of the bashrc into a variable.


