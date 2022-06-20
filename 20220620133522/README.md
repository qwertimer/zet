# Interfacing plex with tailscale in docker

I have often wanted to configure plex to be accessible everywhere but
not having to worry about port forwarding on the router and dealing with
all those issues. I found i often lost the network connection or
something failed on me. I then moved to using plex in a container to
remove the issues i had with installing plex locally. Once this was
configured i needed a way to configure it for use everywhere. I found
that if i run a tailscale node in the plex docker-compose i am able to
connect to the server remotely. This design is super simple and will
allow me to play around with having a dedicated code server or hosted
service connected to the tailscale service.

