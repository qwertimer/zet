# Rob has an awesome help command that outputs as a man page


While watching rwxrob today i noticed he had created an amazing help
tool for use with his zettelkasten project. I had to borrow it. This
tool will sit in my snippets and be added to any larger code base that i
write. I also plan on pythonifying this code at some stage to use it as
part of my python pipeline. The code is below. This should be linked
with completion and delegation which i have stored as scripts in my
snippets repo. These scripts will form part of a base for all my bash
scripts. 

This first block creates a `pandoc` designed man page for the command
that is called.
```
 _make_html() {
  local name=${1:-main}
  local title="$EXE $name"
  [[ $name = main ]] && title="$EXE"
  pandoc -s --metadata title="$title" \
    -o "/tmp/$name-help.html" <<< "${help[$name]}"
}
```
The next command opens the web page for the designated command when
called. This can be done by sending <program> help <command>.
```
x_help() { 
  local name=${1:-main} 
  local file="/tmp/$name-help.html"
  if [[ -n "$HELP_BROWSER" ]];then
    _make_html "$name"
    exec "$HELP_BROWSER" "$file"
  else
    pandoc -s -t plain  <<< "${help[${1:-main}]}" | more
  fi
}
```
To write a help description we initially declare help with 
`declare -A help`
and populate it with
```
help[command]='This is the help for this command'

```


We can also add a little bit of fanciness to the default call of a
script with the below command.

```
x_usage() {
    local cmds="${COMMANDS[*]}"
    printf "usage: %s (%s)\n" "${0##*/}" "${cmds// /|}"
}
```
It will produce a nice usage list of all the methods.

