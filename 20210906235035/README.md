# Quick start with docker

Docker is an incredible tool useful for testing and experimenting with
new programs without breaking your main machine. Docker works
fundamentally by making use of `cgroups`, `namespaces` and `chroot`. Along
with additional functionality through networking and port forwarding.
One can start their journey in docker with a couple of simple commands.
To start a docker container we can either pull down and image and then
start or simply run. Below are the three main ways to get up and running
with a container. 

The first pulls down the docker image using docker pull where image is
the path to the docker image from docker hub or similar sites. Then we
can run the image with `docker run`.

```bash
docker pull <image>
docker run -it <--rm> <--name test> <image>
```
The switches to note in this command are:
```
-i #attach stdin to container (if this is not added we can't interact
with the terminal)
-t #allocates a pseudo tty (Same interface as terminal on linux)
--rm #Removes the container after exiting (Optional and will remove any
files or configurations made to the container.
--name #Optional name to use when attaching and reattaching to the
container
```

The next command is similar to above and can be run alternatively to the
above command. The docker run command by itself will look for the image
locally otherwise will look on docker hub. The -it is outlined above.
```
docker run -it <image>
```

This next command can be used if we have pulled down an image and created
a container with a `--name` switch. This command allows us to attach and
reattach to the container. 
```
docker start -ai test
```
The switches here are similar to the run command:
```
-a #attach to STDIN, STDOUT and/or STDERR (can attach to one or all of
these)
-i #keep STDIN open even if not attached.
```

**Extensions**

There are many additional switches one can use when running a docker
container. Below outlines a few of these and the syntax for them.

```
-d #detached mode 
-p 80:80 #port forward port 80 from the container to port 80 on the
host. If we do not add values to the port it will publish all ports.
   * format  - hostport:containerport (can be a range of values)
--privileged #enables access to all devices on the host. 
--device=/dev/** #Where ** can be any device, enables a single device
access to the container.
--entrypoint #sets an alternative entrypoint to the container. (Specify
what executable to run when container starts.)
--tmpfs #Create a tmpfs mount with options
   * --tmpfs /run:rw,noexec,nosuid,size=65536k #mounts the tmpfs onto
     run with additional options.
-v #Bind mount a volume
   * host-src:container-dest
--mount #similar to v. Additional advantages are simplicity in reading
   * --mount type=bind,source="$(pwd)"/target,target=/app,readonly 
--init #Adds an init system to the container (default:docker-init which
is https://github.com/krallin/tini) ## Useful as it reaps zombie
processes
--network="host" #Gives the container full access to the local system
services such as dbus **use with caution**
```

We can attach to a running container with
```bash
docker attach <name>
```

We can also stop containers that are detached with 
```bash
docker stop <name>
```

This is just the basics of running docker containers. There will be
another post about how to create your own containers and building
multistage builds.
    #docker

