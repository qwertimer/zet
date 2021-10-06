# Using xev and awk to view keypress values

Today i was working on fixing up my sxhkd configuration for keybindings
and i wanted to have a help menu display when the user runs `super ?`,
this binding is simple and makes it easy to remember however sxhkd did
not use ? and could not understand what i was trying to send. The `xev`
program saved my time and gave me an excellent setup for future
keybindings. Linked with awk i was able to strip away all of the
unneeded information and provide only the key number and the string
output of the keypress. This allowed me to find out that the ? is
question for use in sxhkd. The script is very simple which i have added
here. On Ubuntu xev is already installed which makes it super simple to
configure.

xev | awk -F'[ )]+' '/^KeyPress/ { a[NR+2] } NR in a { printf "%-3s %s\n", $5, $8 }'


