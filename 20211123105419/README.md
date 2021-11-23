# Using sys folder to access system information

Inside the sys folder you can get access to a large amount of system information, for example we can find out how much storage exists in the system.

```bash
declare -i Sectors=0

for Dir in /sys/block/*; {
  [ -d "$Dir" ] || continue
  Sectors+=`< "$Dir"/size`
}

Result=$(( (Sectors * 512) / 1024 / 1024 ))
printf "Total: %'d GiB\n" $Result

```

This script scans all the files in the block folder and adds the size of the directory to the sectors. This is then converted to Bytes and then to GiB.

We can also access CPU core temperature in the sys folder. This is found in class and hwmon. Inside this folder we can find the core temperature of the CPU as well as each core.

We can also access the wireless transmission and recieve information in /sys/class/net/wlan0/statistics allowing us to monitor data io over the network.

There is so much inside this that it is worthwhile spending some time looking through it.

