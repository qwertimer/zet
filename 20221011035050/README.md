# Using netstat to find port usage

To quickly identify the ports that are in use we can use `netstat --tcpn`
to get a quick overview of running processes related to the port. The
tcp flag allows the system to search only tcp ports whilst udp can be
called with `-u/--udp`. We can further constrain the command with
`-l` for listening devices, and `-p` for showing the PID of the
program. From here we can grep for our port and undertake further
processing.

