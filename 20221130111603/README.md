# Working with os/exec in Go

One of the interesting things about Go is in some situations we have
output which is counter to my understanding in python. For example
running the ping command in python i would run the command with
subprocess.Run or similar and then i would parse the result. In Go
however if i want to view the result of the command that was run i need
to attach the Stdout and stdErr to variables. This makes sense once you
think about it but the logical code looks different. For example

```Go
pingExecutable, _ := exec.LookPath("ping")

  pingCommand := exec.Command(pingExecutable, ip, "-c", "1", "-w", "3")
  out, _ := pingCommand.CombinedOutput()
  pingCommand.Run()
```
Runs the ping command on an ip address but the CombinedOutput command is
attachhing to stdout and stderr.

