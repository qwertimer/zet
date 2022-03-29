# editing a remote file directly in local vim

Found out you can edit a file on a remote host using vim with
`vim scp://user@host//etc/fstab` where //etc/fstab is the remote file.
This is very useful to work with programs on a remote system.
