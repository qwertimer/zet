# forward a docker program to the display with -v

If you want to have access to a containers GUI program you can forward it using  `-v /tmp/.X11-unix:/tmp/.X11-unix` and `-e DISPLAY=unix$DISPLAY`
These will forward the containers GUI to the host display. If it doesn't work we can run `xhost local:root` to make sure it is forwarding.

