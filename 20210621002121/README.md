# lsio have created a container called webtop

The company linuxserver.io have built a container that is a full linux system
with a window manager and standard system utilities inside a web browser
I plan on updating this dockerfile to incorporate my own configurations to have
the fully fledged development environment for testing and experimentation.

Some of the hurdles may be working with the jetson board. As the architecture
is different. There are benefits to this design. We are able to create a solid
starting point for an image and provide the ability to update the system.
However the disadvantage is if the container breaks you have lost the
additional configurations.
