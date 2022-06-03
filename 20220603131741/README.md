# Useful python profile tool chain

When trying to figure out where i was spending the most time in my code
today i was running simple timeits all over the code. Looking at mcoding
on youtube tonight i found a useful design that may allow me to get
better insights into the code. The first is to run the basic python
profiler which is called with importing cProfile. Then using a context
manager we run the code block that we want to analyse. Once done the
code outputs statistics that we can view with pstats by importing pstats
and sorting the data by TIME.

```python3
import cProfile
import pstats

with cProfile.Profile() as pr:
    cool_func()

stats = pstats.Stats(pr)
stats.sort_stats(pstats.SortKey.TIME)
stats.print_stats()
```

We can then dump this data to a file and use a super useful web based ui
to view this data, called snakeviz.

This will help improve many of my coding issues.




