# Sourcing programs with source and .

The reason we use the source command including the more portable command
`.`(posix) is to change the current processes environment and variables.
Normally when we execute a program from bash it spawns a subprocess.
This process is not able to change the parent process in any way and so
if we change the environment variables the parent process won't see the
change. We see this when we source the bashrc file and similarly when we
source /venv/bin/activate which runs a group of modifications on the
command line and sets some environment variables. It is convention to
never make your sourceable files executable and if you wish to use
syntax highlighting place a dummy shebang to indicate bash but a fake
directory structure.

