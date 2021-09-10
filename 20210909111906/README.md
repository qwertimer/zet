# Go - 100daysofCode -- Day 3

Finishing off the tutorial from yesterday

**Adding Tests**

Go has built in support for unit testing to make it simple to test as
you go. To create a test code block we create a file with `_test` to
tell the Go test command to execute the test functions.

We create a greetings_test.go inside the greetings directory, the code
is seen here.
```go
package greetings

import (
    "testing"
    "regexp"
)

// TestHelloName calls greetings.Hello with a name, checking
// for a valid return value.
func TestHelloName(t *testing.T) {
    name := "Gladys"
    want := regexp.MustCompile(`\b`+name+`\b`)
    msg, err := Hello("Gladys")
    if !want.MatchString(msg) || err != nil {
        t.Fatalf(`Hello("Gladys") = %q, %v, want match for %#q, nil`, msg, err, want)
    }
}

// TestHelloEmpty calls greetings.Hello with an empty string,
// checking for an error.
func TestHelloEmpty(t *testing.T) {
    msg, err := Hello("")
    if msg != "" || err == nil {
        t.Fatalf(`Hello("") = %q, %v, want "", error`, msg, err)
    }
}
```
The code uses the Test name at the start to show `go test` which
functions to run which is really neat. Test functions always take a
pointer to the `testing.T` type. We can add verbosity to the test with
`-v`

**Compile and install the application**

We have two commands to use once the program is completed, we have `go
build` and `go install`.

Running the `go build` command will convert the program into an
executable and be able to be run with ./<program>. The alternative
method `go install` will create an installed package on your system in
the directory that is set with `GOBIN`, to set `GOBIN` we can use `go
env -w GOBIN=/path/to/your/bin` 

Running `go install` will create a program that is able to be run by
calling the name.


