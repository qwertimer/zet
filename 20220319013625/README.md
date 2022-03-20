# Use `newgrp docker` to remove the need to restart computer

When updating usermod, many examples tell you to restart the computer
for the changes to take effect. If you don't want to do that you can
  force an update by changing your user to the group by running `newgrp
  <group>` allowing you to run the commands. Ultimately you want to
  restart to get the configurations working but to initially run tests
  just use the `newgrp` command.


