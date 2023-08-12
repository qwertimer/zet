# Linux has an install command

There is a neat linux tool called install which will take a file and
make a copy of it. Once it is copied it will change the permissions to
`+x` to make it executable. An important switch is `-s` to strip all the
symbols from the binary file. We can also set the `-o` for owner, `-m`
for mode, `-g` for group.

