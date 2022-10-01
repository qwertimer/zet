# Use ithub.com/pkg/errors to wrap errors up the call stack

Often errors are lost in Go as the error is propagated up the call stack
using `errors.Wrapf` one can add context to the error being wrapped to
provide information at a later point in the code when errors are
handled.

