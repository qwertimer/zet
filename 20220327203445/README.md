# Default configurations for ufw

It is always useful to configure ufw upon a new system install.
Below outlines the quick configuration steps for the system.

To begin we install ufw. Once installed we enable and start ufw. This is
seperate to the ufw daemon which is started with systemctl. The start
commands are 
```
sudo ufw enable
sudo ufw start
```

Next we setup the systemd configuration with:
```
 sudo systemctl enable --now ufw
```

The basic configurations that we set are to allow ssh and http/https
with
```
sudo ufw allow ssh
sudo ufw allow proto tcp from any to any port 80,443
```

There are many other things we can allow or deny in this system but
this is the bare necessities when configuring ufw.
