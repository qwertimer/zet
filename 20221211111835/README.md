# Go Concurrency

* Waitgroups
primitives or channels
A waitgroup is part of sync package, starting point where goroutines
start and a point further along that waits on the completion of
goroutines.

To add to a waitgroup
``` 
  wg.Add()
```

Don't make deadlocks, this can be fixed by making sure we have the same
amount of Adds as Done. If we have too many Dones we cause go to panic.

waitgroups should always pass as a pointer rather than a value.




