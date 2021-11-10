# vim command shortcut to save readonly files.

I found this excellent vimrc snippet today. `command! W execute 'w !sudo tee % > /dev/null' <bar> edit!`

This command does the sudo tee command that i have been doing to save readonly files but rather than typng it out i can just `:W` which makes sense in a force write kind of way. I still need to make sure i use the command every now and then so i don't forget it.

