# Use `"${EDITOR:=vi}"` to create a shorthand for `EDITOR=${EDITOR:-vi}`

This doesn't work directly in a script. We can't just write "{EDITOR..."
we need to include a command at the start which sets the value and
returns true. Commands that can do this are `:`, `[`, `test` and `[[`.
This was tested on rwxrob.tv where we worked through what : does at
start of these commands in robs scripts.

See robs zet for more info - https://github.com/rwxrob/zet/tree/main/20210825172754

