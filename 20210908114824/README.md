# Go - 100daysofCode -- Day 2

Continuing https://golang.org/doc/tutorial currently at:

** Return a random greeting **

The first thing to look at in this new section is the Go slice. Much
like arrays in python. The code will create a slice of strings and
return a message randomly.

```Go
package greetings

import (
    "errors"
    "fmt"
    "math/rand"
    "time"
)

// Hello returns a greeting for the named person.
func Hello(name string) (string, error) {
    // If no name was given, return an error with a message.
    if name == "" {
        return name, errors.New("empty name")
    }
    // Create a message using a random format.
    message := fmt.Sprintf(randomFormat(), name)
    return message, nil
}

// init sets initial values for variables used in the function.
func init() {
    rand.Seed(time.Now().UnixNano())
}

// randomFormat returns one of a set of greeting messages. The returned
// message is selected at random.
func randomFormat() string {
    // A slice of message formats.
    formats := []string{
        "Hi, %v. Welcome!",
        "Great to see you, %v!",
        "Hail, %v! Well met!",
    }

    // Return a randomly selected message format by specifying
    // a random index for the slice of formats.
    return formats[rand.Intn(len(formats))]
}
```


We also find some other interesting things in this script we have a
`time.Now().UnixNano()` which looks like it gets the current time in
nanoseconds. We have a `rand.Seed` and `rand.Intn` giving access to
random generators. The tutorial outlines a couple of important
notes. The first being that if you start a function with a lowercase
letter the code is only accessible inside the package. Slices omit the
size of the array which is handy. 

init functions are executed automatically on startup, after global
variables are initialised.[effective go](https://golang.org/doc/effective_go#init)

** Return greetings for multiple people **

Adding support to great multiple people. In other words handle a multi
value input.

It is important to not break functionality of your code by changing
the base functions and so to update with the new functionality we
create a new function.
```Go
// Hellos returns a map that associates each of the named people
// with a greeting message.
func Hellos(names []string) (map[string]string, error) {
    // A map to associate names with messages.
    messages := make(map[string]string)
    // Loop through the received slice of names, calling
    // the Hello function to get a message for each name.
    for _, name := range names {
        message, err := Hello(name)
        if err != nil {
            return nil, err
        }
        // In the map, associate the retrieved message with
        // the name.
        messages[name] = message
    }
    return messages, nil
}
```
* This function introduces a for loop with error checking. The `range
names` must be similar to pythons range functionality here.
Also of note is the input is a string slice. with a return of a map
of the string string and the error.
* We create a messages map to associate each of the received names (as a
  key) with a generated message (as a value). In Go, you initialize a
  map with the following syntax: make(map[key-type]value-type). See
  [Go maps in action](https://go.dev/blog/maps). Finally we edit the
  hello code to get a slice of names and feed it to the
  greetings.Hellos function.

Tomorrow i will finish off the rest of this tutorial and read
through the links i have provided today.

