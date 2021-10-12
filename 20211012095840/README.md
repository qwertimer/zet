# Use pv to add a progress bar to any pipe.

If you want a progress bar in any linux command pipe the file into `pv`
and then send the output to the required location.

For example if we want to copy an iso onto a drive we can use the below
command.

```
cat arch.iso | pv > /dev/sdc
```

This above command is also the better way to write isos to drives rather
than using `dd`.
