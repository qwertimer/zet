# Parallelising a process in bash

If we have a process that we want to parallelise we can use a simple script to parallelise the process and limit the number of processes with the N variable
This allows us to spawn multiple versions of the program but limit resource usage with the variable. If we want to run all the items at once we can just use the `&` symbol to send each process to the background.

```bash
#!/bin/bash

N=6
(
for item in "$@"; do
  ((i=i%N)); ((i++==0)) && wait
  python3 safaribooks.py "$item" &
done
)
```
