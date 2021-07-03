# Learning Go [part 2]

- We export go functions by making the function begin with a capital letter. The
compiler also finds the main function of the main package when we execute go
code.

- It is mandatory for a go program to be part of a package. Every package should
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
   - `append` - adds to the slice.
   - `copy` - copys from one slice to another.
- `map` is a key value pair. ie a dictionary in python. 
   - `map` is unsorted.
   - `len` - returns length of `keys`.
   - like python to change a `map` we use `numbers["one"]=11`
   - `delete` - deletes an element.
   - `make` - memory allocation for built in modesl. - such as `map`, `slice`
     and `channel`. while `new` is for types memory allocation.

### ----------------------------------- Loops ----------------------------------

- `if` doesnt need parentheses.
   - `if x > 10 {`
- `goto` is available --- don't use. - however it is a goto to a name. 
- `for` - is available but there is no `while` or `do while`.
   - `for` is done the same way as in c....
   - `break` and `continue` is available.
   - `for` can read from a slice:
       - `for k, v:= range map`
-  `switch` -`case` normal method.
 
### --------------------------------- functions --------------------------------
- functions have `arg ...int` - which acts like `*args` in python.
- When `x` is passed the value doesn't change. If we actually want to change
     the variable we need to point to the location with a pointer using `*int`.
     We pass the value with `&`.

- `defer` - postpones the execution of a function till calling function has
     finished executing. `defer` works in reverse order when the program weaches
     the end. This would be useful when catching errors and closing the files. 

- Functions are also variables in Go. Defined by a `type`. Functions are first
     class citizens.

### ---------------------------------- Imports ---------------------------------

- import by absolute path. `$GOPATH/pkg/shorturl/model`
- We can use a `.` when we improt to have the package name ommited when we call
  it. 
    -   `import (. "fmt")`
    -   `Printf` rather than `fmt.Printf`
- We can alias `f "fmt`

### ---------------------------------- Structs ---------------------------------

- We define structs similar to C.
     - `type Product struct {`
          `name       string`
          `itemID     int`
          `cost       float32`
          `}`
- We init structs with `var gobook Product` and can put values in locations
  with `.` notation. `gobook.name = "web book`
- We can also `:=` assign. init struct with order `book:= Product{name:"book",`
  `itemID:10025`
- We can have `sub` structs which essentially is inheritance like python. 

### ----------------------- Methods (OO type paradigms)  -----------------------

- A method is affiliated with a type it contains a `receiver`.
- `func (r ReceiverType) funcName(params) (results)`
- We can use this to create multiple functions of the same name by calling a
  struct as the `receivertype`
 
### ------------------------------- Other things -------------------------------

- defining custom `types`: `type typename typeliteral`


### --------------------------------- Out Notes --------------------------------

-- All these notes have been derived from the excelent book. -- https://thewhitetulip.gitbook.io/bo/

  


