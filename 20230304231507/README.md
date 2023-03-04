# Build conditions in Go

We can actually utilise a build condition using the suffix name of a
file to build for specific operating systems. For example we can build
a file for linux with `_linux` and mac with `_darwin`.

We can also utilise build tags at the top of a file to build only for
specific OS and architectures. For example we can use `//+build
darwin,!arm64` to build for mac and amd64 chipsets or use `arm64` to build
for arm.

