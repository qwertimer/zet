# Anonymous functions in Go

The syntax for anonymous functions in go is interesting. 
The main idea of the anonymous function is to run a function as a
closure or part of a goroutine. The syntax of a basic anonymous
function is:
```
func(){
  //Do something
  }()
```
We can also assign a function to a variable which doesn't include the
`()` at the end. We can then call the variable later with the `()` at
the end.

We are also able to pass variables into the function.

