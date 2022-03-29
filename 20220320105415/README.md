# Use run-parts with a folder to run all the iterable files

When you have multiple run scripts such as 00- 10- 20- 35- use the
run-parts with the folder and you can run all the scripts inside the
folder in iterable order.

```bash
run-parts /etc/update-motd.d/
```
Will run all of the below scripts.
```
/etc/update-motd.d//00-header
/etc/update-motd.d//10-help-text
/etc/update-motd.d//50-motd-news
/etc/update-motd.d//85-fwupd
/etc/update-motd.d//88-esm-announce
/etc/update-motd.d//90-updates-available
/etc/update-motd.d//91-contract-ua-esm-status
/etc/update-motd.d//91-release-upgrade
/etc/update-motd.d//92-unattended-upgrades
/etc/update-motd.d//95-hwe-eol
/etc/update-motd.d//98-fsck-at-reboot
/etc/update-motd.d//98-reboot-required
```

