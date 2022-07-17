# Extracting app images and moving the Application to /usr/bin

Looking at nvim installation they suggest running an app image. Im not a
fan of app images i prefer the package to be installable via apt. If
however there is no apt candidate i will use appimages over snap
packages. I found out today nvim has a neat setup to extract the
appimage and mv it somewhere usable and create a symlink in the user
path. This way i have a full application being called with the standard
command. For example, nvim works directly from the terminal in all
locations.
- nvim example

```bash
./nvim.appimage --appimage-extract
./squashfs-root/AppRun --version

# Optional: exposing nvim globally.
sudo mv squashfs-root /
sudo ln -s /squashfs-root/AppRun /usr/bin/nvim
nvim
```

This could probably also be done with a direct ln of the appimage but i
like this solution better.


