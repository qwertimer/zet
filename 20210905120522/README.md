# Use ctrl \ to close python script if blocking Ctrl C

If you ever find your self in an infinite loop being unable to close the
program running using `ctrl \`` will send sigQuit to the program causing
it to core dump. This can occur when you have a blank `except:`
statement in python. To over come this error using the `except
Exception:` instead you wont cause this issue in your python program.

    #python #sigquit 

