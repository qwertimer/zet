# Process substitution or <()

The `<()` is known as process substitution which creates a file of the
form `/dev/fd/63` instead of using `stdin`, this makes a file called a
named pipe. which redirects the output of the command to the named pipe.
Often this is used in conjunction with a `<` to send the result of this
into `stdin` of another function. This can also be used in a while loop
where the results of the process substitution is fed into the loop. This
would usually be fed into the read function.

An example of this is:

``
while read -r line; do
    [[ $line =~ ^declare\ -f\ x_ ]] || continue
    COMMANDS+=( ${line##declare -f x_} )
done < <(declare -F)
``

This function is dense but basically it reads in all the functions of a
file using <(declare -F), technically being saved to `/dev/fd/63` or
similar. This is piped in as `stdin` to the while loop.
Inside the while loop we test whether the line starts with `declare -f
x_` if so then remove `declare -f x_` from the line and save it into the
COMMANDS array. 

