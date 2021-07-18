# Stat command will give the mode of a file

We can use the stat command to check the mode of a file ie. 600 or 700. We can then use this programmatically for example 
`if [ stat --format '%a' /swapfile -eg .... ]` will allow us to check a files mode and run commands based on it.


