# Learning vim copy, paste and registers to stop deleting things

Often times i am editing a file and yank a line only to press `dd` and overwrite the yanked line. To overcome this i need to use `"` followed by a letter. This can be used with `y` to yank and `p` to paste. This allows me to save multiple items to an array of clipboard locations and call them back later.

The registers are used to store cut and copied information as well as macros. It is wise to use some level of design to keep and use both macros and yanks without overwriting one or the other.

