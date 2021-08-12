# I have reached a point in my linux understanding

Today i was working through cleaning up `CDPATH` when i realised when i
`CD`'d into `scripts` i had somehow moved into the scripts symlinked
inside the scripts folder. I didn't know whether to remove it or not and
was hesitant about removing it, i decided for safety i would confirm the
file i was going to delete was symlinked and used short circuit logic to
check that it was a symlink and if so remove the folder. This was done
with
```
[[ -L ./scripts ]] && rm -rf ./scripts
```

A simple in line shell script to confirm i was deleting the write file
and not my scripts directory.

