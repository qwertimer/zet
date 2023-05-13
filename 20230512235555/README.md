# Using registers in vim and vscode properly

## Saving to register
To save to a register we use the `"` symbol followed by a letter or
number and `y` to yank into that register

## Loading from register
To load from a register we use `"` followed by the above letter and `p`.

## Viewing the register

In vim we can view the register with `:reg` or this can be mapped to
something like `<leader>r`.

## Macros are stored in vim registers

One thing to note is if you use a lot of macros you can overwrite them
by saving to the register with your yank.
