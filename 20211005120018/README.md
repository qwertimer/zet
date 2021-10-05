# Use the -L option in curl to download github releases

I often want to download and install packages from github to test  out a
program and often these packages arent available from apt or other
managers. Sometimes i pull down the full package and compile it but this
isnt always an option especially in debian based systems. With arch i
can run git repositories through any AUR helper and build the package.
Whilst i do not know of a way to do this is Ubuntu. Instead i found
today i can use the `-L` on the releases link and it will pull it down
with curl. This saves me from downloading the file to my downloads
folder moving the file to somewhere else and running the installation. I
can now do it all from the command line.

