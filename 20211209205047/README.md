# Vim tricks: Using gf to open file below cursor and extending it with a new mapping

`gf` is a fast tool to open a file that is being used in the current vim buffer. For example if i am working on a python program and i have a config file that i am accessing, if i hover over the file directory, `gf` will open the file. 
If the file doesn't exist `gf` fails. To make it open non existent files for editing we add to the vimrc `map gf :edit <cfile><cr>`.

