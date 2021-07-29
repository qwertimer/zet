# Brace expansion could be used for making files in directories

Not just making files in directories but we can use brace expansion `{}`
along with prefixes and suffixes to create names and strings. The main
idea of this is that you begin with a prefix `pre{` before the brace
followed by comma separated strings or numbers. You can add `[incr]`
inside to increment the values by the `incr` mark. Finally you can have
a suffix following the brace `}suff`. Below is an example.

`echo b{a,e}n{a,u}n{a,e}`
resulting in:
`banana banane banuna banune benana benane benuna benune`
