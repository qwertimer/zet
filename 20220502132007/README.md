# Quick tutorial on chroot to fix a broken install

The first thing to do is configure the drive to be mounted in the live
disk or host computer. This may be through numerous methods. If there is
no encryption you can just mount `/dev/<deviceID>` into a folder like
`/mnt/faulty_drive`. If there is encryption on the drive you first must
decrypt the device, this is done using `cryptsetup open` followed by the
device and an identifier such as `cryptsetup open /dev/sda ubuntu` Once
this is donw you can mount the `ubuntu` to your `/mnt` location using
`mount /dev/mapper/ubuntu /mnt/faulty_drive`. If you are also using lvm
it becomes a little more difficult and you need to have lvm2 installed.
From there run....


Once the drive is mounted. Bind mount the dev
folder and mount proc, pts and sysfs with 
```
mount -t proc proc /rescue/proc
mount -t sysfs sys /rescue/sys
mount -o bind /dev /rescue/dev
mount -t devpts pts /rescue/dev/pts
```

This allows the system to interact with the processor correctly. Next we
make a backup of the `/etc/resolv.conf` file and create a newfile with
`echo "nameserver 4.2.2.2" > /etc/resolv.conf` This will provide dns
resolution allowing you to connect to the internet in the chroot.
Finally you are able to chroot into the drive and run commands as if you
were in the system.
