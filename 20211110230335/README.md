# Using realpath when creating symlinks

If i have some crazy nested folder location like my .dotfiles folder
rather than writing out the whole directory i can use
`ln -s "$(realpath <filename>)" <dest dir>`
Whats great about this is it becomes super fast to set up all my
symlinks. It doesn't work for scripts though.

