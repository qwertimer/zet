# Learning some bash - Part 1

These notes are mostly from Day 14 - 16 of the beginner boost from Rob... 
In bash you are able to run any command found in path. This is very important and you should never overwrite a linux program with your own names. This was seen when rob created in the past a program called main (changing to main git branch). When he tried to show what would happen if you moved the main call above the subprocess (functions) it tried to call the system main program and failed (VERY DANGEROUS).

Other things of note. `$1 $2 etc` are used to move variables around the program. $1 will be the fist passed variable and so on. You can use `$#` to get the total number of  variables that are passed at once. You can use `$@` To get "first" "second" ... and never use `$*` unless you are meaning to concatenate all the values into one arguement string.
You are able to return strings with a work around where you echo the result of what ever the script is and using $(<subprocess>) you are able to capture the result of this and pass it on to other locations.

