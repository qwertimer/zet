# Use `"$(<"file")"` instead of cat inside scripts

If you want to reduce the need for spawning subprocesses and piping the
results of cat into a variable you can use `"$(<"file")"` to cat out the
file.

If you wish to read to an array you can use `IFS=$'\n' read -d "" -ra
file_data < "file"` or in later versions of bash `mapfile -t file_data <
"file"`
