# Working with the bash completion tools from rwxrob

One of the commands rob uses will check if the input is the executable
name which will then run that command. This is useful for setting a
default option. For example i have an ix2me command that will run the
command at command line with `ix2me <url>`. This can also be run by `ix2me
ix2me <url>`. The benefit of expanding these programs is to generate a
help functionality into all the scripts.


The function is shown below:
```
for c in "${COMMANDS[@]}"; do
    if [[ $c == "$EXE" ]]; then
        "x_$EXE" "$@"
        exit $?
    fi
done
```
