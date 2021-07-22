# add a newline to a variable.

We can add a newline to the variable using subshell commands.

nl="\n"
title= ${desc%%$nl*}
