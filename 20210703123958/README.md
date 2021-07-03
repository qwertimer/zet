# Learning Go [part 2]

- We export go functions by making the function begin with a capital letter. The
compiler also finds the main function of the main package when we execute go
code.

- It is mandatory fir a go protam to be part of a package. Every package should
be a distinct folder on `$GOPATH`.

- Go does not have any try catch, it uses one `error` type in the errors package.
We need to handle our own errors.

- Enumerate functionality is done with the keyword `iota`. This starts at 0.

- Array is defined with:
    -   `var arr [n]type`. -- `n` is length, `type` is the type and `[]` to get or
        set elements.
    -   We can nest arrays in arrays.
- Main disadvantage of an array is we need to know the size. We can use a
  `slice`
  instead which is a dynamic `array`.
   - like in python we can do `arr[:n]` to define a section of an array up to
     `n`. We can also define to the end with `ar[n:]`
   - `len` - gets the length of the slice. 
   - `cap` - gets the max len of slice
   - `append` adds to the slice.
   - `copy` - copys from one slice to another.
