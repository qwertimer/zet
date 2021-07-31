# vim copy and paste the right way

The best way to copy a section of code is to save the section to a
`/tmp/<file>` using `:w /tmp/foo1` and then we write it back out using
`:r /tmp/foo`. Another useful shortcut is to just use `!<number>!` and
remove the last `!` rather than use `:`

We can also use the viminfo file to save the snippet. However i do like
the idea of making temp files for things i want to do.
