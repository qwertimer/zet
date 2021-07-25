# chroot, namespaces and cgroups.

In linux we can isolate a process and its children using chroot which
effectively isolates the system from accessing anything at all. For
example we may want to isolate an unknown program from the main system
or fix a broken install we can use chroot. However it is of note that
this jail has no access to any files including things like `ls` and
`grep` so we need to add them in and their dependencies by `cp` the
files from `bin`. We also need to check dependencies with `ldd`. 

This doesnt completely block the user as the jailed root can still see
the processes on the system. To fix this we can create namespaces. To do
this we install `debootstrap` and run 
`unshare --mount --uts --ipc --net --pid --fork --user --map-root-user
chroot /better-root bash` and mount individually mounr `proc`, `sys` and
`tmp` to create an isolated user.

However this doesnt completely stop issues on a multi user server. If we
want to truly isolate users we can use `cgroups` which set the amount of
processes available for the user including CPU and RAM etc. To configure
this checkout
[https://btholt.github.io/complete-intro-to-containers/cgroups]

