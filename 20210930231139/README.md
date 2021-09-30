# Using vipe and vidir from the moreutils package

I found out today about the `vipe` and `vidir` tools from the moreutils
package. These too tools allow vim integration in pipe flows. The first
tool vipe allows you to send a pipe into an editable vim buffer which
can then be used to save as a file on close. For example:

`ls -a | grep .bash | vipe > bash_dotfiles`

allows the output of a grepped ls command searching for bash files to be
piped into a vim buffer where any non .bash specific files could be
removed before saving as a log file or something else. The above example
is silly and mostly pointless but shows the flow.

The second tool `vidir` allows you to edit the output of a find search
and modify filenames or remove files from the directory. This is useful
when you are looking at bulk renaming files in a folder. An example of
using vidir is:

```
find -type f | vidir -
    - Edit all files under the current directory and subdirectories.
```

This tool could be useful when working with old folders.

