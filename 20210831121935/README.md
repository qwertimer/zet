# Multicall or omi-executable programs.

The most famous omni executable program is busybox which is a single
binary containing a large portion of the base linux programs in it. The
design works by reading in the `sys.argv[0]` (python) or `$0`(bash),
into the main program. This program is symlinked to different names for
example we could have the program (called myprog) symlinked to
calculator and time. This program will read in the executable name, i.e.
calculator and feed this into a switch case to determine the code block
to run. 

Below is a simple omni-executable seen on Anthonywritescode, written in
python


```python
#!/usr/bin/env python3

import os.path
import sys

def read_link(path):
    read = os.readlink(path)
    return os.path.join(os.path.dirname(path), read)

def main():
    exe = sys.argv[0]
    while (
        os.path.islink(exe) and
        os.path.islink(read_link(exe))
        ):
        exe = read_link(exe)
    if exe == 'uniq':
        seen = {}
        for line in sys.stdin:
            seen[line] = True
        for line in seen:
            print(line, end = '')
        return 0
    else
        raise Not ImplementedError(exe)

if __name__ == "__main__":
    raise SystemExit(main())

```
