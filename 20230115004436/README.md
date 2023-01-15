# Go structs and struct methods

To create OO like code in Go we attach methods to a struct. An example
of this is when you have the below struct

```go
type Student struct {
  name string
  grades []int
  age int
  }
```

We can then attach methods to the struct and this allows us to use the
variables in the struct and build functionality around it. For example
we have the below method to get the age of the student.

```go
func (s Student) getAge() int {
  return s.age
}
```
We can look at the first brackets as the method acts on the object
student.

To access the method we first need to instantiate the struct to then be
able to act on it. To do this we can call.

```go
s1 := Student{"Tim", []int{20,30,50}, 33}
```

If we want to act on the variables in the struct when we access the
struct in a method call we need to use a pointer to be able to change
the actual values in the instantiated struct. Below is a simple example
of this:

```go
func (s *Student) setAge(age int) {
  s.age = age
```
To use the above method we can call `s1.setAge(80)`

If we don't use the pointer we only change the value whilst inside the
method and on returning from the method the field of the struct remains
unchanged.




