# Go - 100daysofCode -- Day 1

I have decided that i am going to try the #100daysofX challenge and
learn Go over the next 100 days. These posts will sit in the zet folder
but Will follow the same guide as the title of this zet. This way it is
searchable and easily used as a reference. The notes seen here will come
from many sources and some days may have very little if i am looking at
specific code or tutorials.

The following notes come from [golang](https://golang.org/doc/tutorial)

**Getting Started**

When you import packages into your Go program, these are managed in a
go.mod file. This tracks the modules that provide the packages.
To set up a module we use
```
go mod init github.com/hello
```

The fundamental hello world code is completed by declaring that your
package is main with `package main`, following this as is similar in
most languages are our import statements. Go doesn't provide Println, or
print functionality in the main go binaries but it is provided with the
package fmt. We can import a function and then use it. If we don't
use an imported function the program throws an error.

The basic hello world is seen below.
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
    }
```


We can find go help on the command line with `go help`

Extending on the hello world program we can add an external package such
as rsc.io/quote. If we add this into the program and modify the print
statement, when we run the script with `go run .` we get an error saying
no module available, this can be remedied with either `go get
rsc.io/quote` or the more prefered method of `go mod tidy`. This will
find the package and create a go.sum file for use in authenticating the
module.

**Go Modules**

In this example we build a module to communicate with a main package.
The code is seen here:

```go
package greetings

import "fmt"

// Hello returns a greeting for the named person.
func Hello(name string) string {
    // Return a greeting that embeds the name in a message.
    message := fmt.Sprintf("Hi, %v. Welcome!", name)
    return message
}
```
Of note in this code is the package name is now greetings. We also have
a new design for the function, the name is now Hello followed by the
input parameter name and type and outside the brackets is the return
type.

Inside the code we use `:=` which is a go shortcut to declare and
initialize a variable in one go. Alternatively we can declare then
initialise with
```go
var message string
   message = fmt.Sprintf("Hi, %v. Welcome!", name)
```

We also make use of the Sprintf function, which has a format string with
`%v` is the format type being a verb we then substitute the second
parameter in it's place. 

We can then call the package from another module.

To do this we add to the import the module name. In this example case it
is `example.com/greetings`. However as Go tries to search the web for
the package we need to modify the mod file to explicitely indicate the
location of the package. This is done with:
```go
go mod edit --replace example.com/greetings=../greetings
```
This will modify the mod file to indicate the parallel directory named
greetings.

This appends to the end of the mod file a pointer to indicate the
replacement. `replace example.com/greetings => ../greetings`. When using
published modules we can change replace to require and define a
particular version of the package.

**Adding Return and error handling**

We can modify for the greetings package to add in error handling as seen
below:
```go
package greetings

import (
    "errors"
    "fmt"
)

// Hello returns a greeting for the named person.
func Hello(name string) (string, error) {
    // If no name was given, return an error with a message.
    if name == "" {
        return "", errors.New("empty name")
    }

    // If a name was received, return a value that embeds the name
    // in a greeting message.
    message := fmt.Sprintf("Hi, %v. Welcome!", name)
    return message, nil
}
```

The code above shows the error being handled by an if statement. It also
returns early with an error provided by the `errors.New` command. We can
then catch these errors and log to file with the log package. Modifying
the main hello package we can check for errors from the greetings
package and if the program has an error log it and quit, the code is
below.

```go


package main

import (
    "fmt"
    "log"

    "example.com/greetings"
)

func main() {
    // Set properties of the predefined Logger, including
    // the log entry prefix and a flag to disable printing
    // the time, source file, and line number.
    log.SetPrefix("greetings: ")
    log.SetFlags(0)

    // Request a greeting message.
    message, err := greetings.Hello("")
    // If an error was returned, print it to the console and
    // exit the program.
    if err != nil {
        log.Fatal(err)
    }

    // If no error was returned, print the returned message
    // to the console.
    fmt.Println(message)
}
```

The `log.SetPrefix` begins the log file and the `SetFlags` command would
configure other attributes. We catch the error in the assignment from
greetings and run the exit logic.

Tomorrow i will expand on this and finish off the second tutorial on the
golang.org website


    #100daysofGo #Go

