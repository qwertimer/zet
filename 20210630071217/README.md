# Getting Started with Go

Go is a great language. It has some cool features.

The rwxrob How to Start a Golang Project right is very useful -- https://www.youtube.com/watch?v=Ot9Em123Fz8&t=739s
The codecademy go course is good as well - https://www.codecademy.com/courses/learn-go/lessons/

Other interesting Articles
https://medium.com/rungo/everything-you-need-to-know-about-packages-in-go-b8bac62b74cc
https://medium.com/rungo/anatomy-of-modules-in-go-c8274d215c16
https://medium.com/google-cloud/building-a-go-web-app-from-scratch-to-deploying-on-google-cloud-part-1-building-a-simple-go-aee452a2e654



Notes from youtube videos - 


- Begin a project by doing go mod init github.com/<user>/<program>. This will
  initialise a go module.
- `package` is what the program will be named when using it so be careful with
what you name these fuctions.
- If you want to use a functipn from a library it needs to be imported just
like python. If the package is not used GO will flag an error so be careful
with this.
- We have variables and constants in go with the keywords `var` and `const`.
   - To initialise a variable of type string we use :
       - `var message string` 
   - To create a constant we use:
       - `const message string`
   - We can use the := operator to declare and assign the variable at the same
     time
       - `x := 2`
   - If the variable has been initialised we can assign it with:
       - `x = 2`
- Functions are defined using `func`. They should be named with camelCase.
  takes zero or more arguments, which we can define the type. We can follow
  this with a return type declaration to explicitly indicate the type of the
  output variables.
  eg.
  ```
  func valueMod(a, b int)(int) {
  c = a % b
  return c
  }
  ```
  
- Unlike python we have `if` and `else if`
- Always surrond these control flow statements with `{}`
- `switch` and `case` are available.
- We have a single looping procedure with `for` this syntax is similar to c
  syntax. except we can use `for _, i := range d` for iterating over a range.
  Im sure there is more that we can do with this functionality like providing
  any named function....
- When we want to use a function in another program we can `export` it by
  capitalising the first letter of the function. Anything that is capitalised
  is available in the package for other users.
- We have anonymous functions - basically a function that is defined and run
  inside the main function and is not accessible elsewhere.
- We also have Pointers, Methods and Go routines which i will add in a latter
  zet 
  
