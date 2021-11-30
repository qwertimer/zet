# smug - a simple tmux session manager

Smug sets up tmux sessions using a simple yaml configuration file.
The simplicity of this configuration abstracts away from the tmux
default config tools.

To get smug we can download it from https://github.com/ivaaaan/smug.git.

To run this we set up a configuration file which can be stored in
~/.config/smug or pointed to with the `-f` switch. We can use `smug new
`<project>` to create a new configuration file. Then we can start the
tmux ession with `smug start <project>`.

