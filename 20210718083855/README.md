# Check and do something with a file based on its UUID.

From Terminalforlife on youtube i found that you can write a shell script one liner to find files in a directory belonging to a specific user ID and do something with them. The example is shown below.

```sudo bash -c 'for File in *; { UID2=`stat -c "%u" "$File"`; [ $UID2 -eg 1001 ] && rm "$File"; }```

This script searches for all files in the folder and checks using stat for the `UUID` using the `%u` flag. Then tests against the required `UUID`. If this matches then do something. ie `rm "$File"`



