# The absolute power of chroot

Working on the setting up the raspberry pi with my son today. The
computer froze mid update and no longer would boot. Rather than
reflashing and starting again i grabbed the sd card and plugged it into
my main computer. From there i mounted the rpi into `/mnt/rpi` bind
mounted the dev and mounted sys and proc into the rpi os structure.

The code to do this is:

```bash
mount --bind /dev dev
mount -t proc proc proc
mount -t sysfs sysfs sys
```

Once done i used chroot to change the root to the rpi with `sudo chroot
. bash`, from there i was able to fix up the system by updating apt and
fixing the errors that occurred. I then updated all the system as needed
and unmounted the system.

I am now a total convert to using chroot to fix any issues i have with
installations.



