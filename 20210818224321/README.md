# Linux bash expansions

There are many bash expansions available to help speed up movements and
function calls though out linux and bash scripts. Below are some of
these with their explanation.

* `*` - expands the search to include all characters that are available.
  For example if there is a folder with foo, bar and baz in it. If we
  run `ls b*` it will expand to `ls bar baz`.
* `~` - expands to the `$HOME` variable which is usually /home/<user>.
* `~+` - expands to `$PWD` which is the current working directory.
* `~-` - expands to `$OLDPWD` which is the previous directory you were
  in. You can also `cd` to this with `cd -`
* `{}` - will expand what is inside the braces and add it to what is on
  the outside of the braces. For example if you wish to create a
  directory with multiple `txt` files you could use `touch
  {foo,bar,baz}.txt`, will expand to `touch foo.txt bar.txt baz.txt`,
  this also works with the suffixes or prefixes.
* `{1..9}` - will fill in the values in between 1 and 9. This could be
  used to create directories with numbers or letters at the start. We
  can multiple these together, for example {a..z}{a..z} will expand to a
  pair of letter combinations starting at aa and ending with zz. 
* `!!` - Will rewrite the last command to the shell, this is called
  history expansion. This can be useful
  to pipe results into another program.
* `{01..10}` - will expand to 00 01 .. 10.
* `{01..10..2}` - will output only odd numbers starting at one. 01 03 05
  07 09.
