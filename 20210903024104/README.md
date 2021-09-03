# <(something) is a process substitution and creates a named pipe

To further understand the command above the process substitution creates
what is known as a pipe using /dev/fd/<n> and sends the result of the
process within the parentheses to another process. Process substitution
can compare the contents of two directories. Check out
[Process Substitution](https://tldp.org/LDP/abs/html/process-sub.html).

