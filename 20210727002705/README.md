# pywal is a nice tool to generate terminal colour schemes

I have set up pywal to autogenerate a new terminal scheme everytime i
run the command nwal. This is integrated with `urxvt` to create
transparent terminals. I have an alias for wal to be automatically
linked to my wallpapers folder and to output to /dev/null the stdout.
he script i have autoruns pywal on the wallpaper folder with -a set to
70% for terminal transparency.

To install run `python3 -m pip install pywal`

The nwal script is seen below.
```
#!/bin/sh

wal -a 70 -i ~/wallpapers/wallpapers >>/dev/null

```
