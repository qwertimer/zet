# Globbing in terminal

Globbing is an excellent resource for working with folders and files in the terminal.


One of the great things about globbing is that you can create a set of files using
`file{01...10}.{md,txt}` will create 20 files with md and txt for 10 individual files. This is very useful when running tests or other such quick scripts.

## Globstar
`**/*` will find all files in the directory.
`find` is a better resource with regular expressions.

## Ranges
`ls f[ao-q]*` will match anything with an f and a group of values a and range o to q.

## Match files that don't contain value
To find all files that don't start with a value. using `ls -d [^.]*` will find all files that don't start with .


CODE BLOCK:
`for i in [^.]*; do echo "$i"`
