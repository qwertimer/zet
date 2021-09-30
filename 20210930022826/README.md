# Separate single run bash profile from run each new shell with .profile

The .profile and .bash_profile files were originally intended to be run
on startup to process single setup environment variables that in the
past would have taken a long time to run. This is not much of an issue
with current computers but does in fact present a good workflow habit.
Separating single run scripts such as starting the ssh-agent or
other scripts remove issues of spawning multiple agents or other such
daemons. Other benefits of this design is to implement
overwriting scripts such as language settings by changing this in the
bash_profile on user login. For more information and an overview i found
this link to be very useful.
[dotfiles](http://mywiki.wooledge.org/DotFiles)

This approach is probably an excellent way to source programs such as ROS and run one time configurations on
startup..

