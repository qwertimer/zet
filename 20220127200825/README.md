# Ensuring docker reruns updated code

Docker uses the cached images each time you rerun a build. IF you have changed the underlying shell script or other script docker doesn't know this and will use the cached version instead. To overcome this we can do a couple of different things. The first is to use `--no-cached` which will force a rebuild from the start. This is frustrating as it removes all the basic scripting that you would do in the container and forces the system to rerun apt update etc. 
The second setup is to encapsulate your changing script with a run script that sources the host file. This will ensure the latest version is copied into the container at build time. 
The final design that i use most frequently is a no-op command. This can be commented in and out at each new build which forces the build system to rerun on each build from the no-op point on. The simplest no-op is `RUN :`.


