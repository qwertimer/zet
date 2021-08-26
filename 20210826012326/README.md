# Using Grep in bash without actually calling grep

Watching Robs steam today he wrote an excellent grep tool in bash. We
can apply this to many setups and it may be useful to make this into a
filter.

The script is:
``` bash
while IFS= read -r line; do
  [[ $line =~ ^RE ]] && echo "$line"
done < <(ls -1)
```

This helps to remove subprocess calls to grep and will be useful for so
many things.

  #bash #grep #scripting


