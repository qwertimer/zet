# IO redirection in linux

I often make a mistake when using these redirection commands. I have on
numerous occasions accidentally overwrote a file with the result of a
command. So i have outlined them below to remember them for the future.

The first for standard out. We have two symbols. The first is `>` which
writes the result of the left hand side into the right hand side. This
is used for creating files mostly. The second symbol allows us to append
to a file. This symbol is `>>`.

The second set of symbols is for standard input.These symbols are the
`<` and `<<` symbol. The first is used in commands that accept input
from stdin. We can redirect a file for example into the stdin. For
example if we have a file with a list of values we can send it to sort
with `sort < file_list.txt`. The next symbol is known as the here script
or here document. This is denoted by `<<`. This is used in conjunction
with a token to denote the start and end of the information being fed
into the command on the left hand side. For example we can run:
``cat << EOF
 This is a rhyme
 It doesn't need a line
 because we are out of time.
 damn fine.
 EOF``

In bash we also have `<<<` which means the here string, which will pass
the words on the right to the standard input command on the left.

We also have pipes `|` which send the standard out of one command to the
stdin of another command. For example we can send:
`cat "apple.txt" | lolcat` which will send the output of apple.txt to
lolcat.
