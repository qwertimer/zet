# The difference between Process Substitution and Command Substitution

The process substitution `<(echo 'Hi')` and command substitution `$(echo
'Hi')` are used in many shell scripts and i could never understand what
the use of a process substitution does. A terminalforlife video has
given me more understanding of the differences between these and why you
would use one over the other. The command substitution is seen often in
many programs often used to get the output of a command and send it
`stdout`. Using process substitution correctly can be seen below.

```bash

cat <(echo hi)

#equivalent
#cat FILE
#FILE = 'hi'
```

Using command substitution:

```bash
cat <<< "$(echo hi)"
```

However it is often seen where people will send the result of the
process substitution to `stdin` with the `<` such as `cat < <(echo hi)`.
If you want to send the pretend file to stdin this is the incorrect way
to do it. Instead we can use the command substitution with a here string
`<<<` with a command such as `cat <<< "$(echo hi)"` which translates to
sending `echo hi | cat` where cat reads stdin. However if a program is
unable to use stdin into the program but is able to read a file we can
use process substitution to make the process look like a file. This is
because under the hood the process substitution creates a FIFO or file
descriptor. The file descriptor or named pipe is a file found in
`/dev/fd<n>` where `n` is a number. 

One thing to note that was mentioned in the comments is that the process
substitution is useful when we are reading line by line of the file and
will process each line as it arrives whilst the here string with command
substitution waits on reading the whole file.

    #bash #process-substitution #command-substitution

