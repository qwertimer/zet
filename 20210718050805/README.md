# Removing files or directories neatly

Just found that you are able to use a nice shell snippet to remove either files, directories or symbolic links using some short shell scripting.
`for Dir in *; { [ -d "$Dir" ] || continue; rm "$Dir"; }` This one liner checks all `files` in the directory and if it is a directory using the `-d` command or `-f` for files or `-l` for links. run the remove command otherwise (`||`) skip the file

