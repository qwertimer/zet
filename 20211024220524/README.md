# Reinforcing what i have learnt by using it in the terminal

I have learnt a huge amount in bash and am beginning to see how powerfull the bash knowledge can be for working with linux.
However i often write a script to do something and then just run the script. This is great for having goto commands at my disposal but some times i should write the command out rather than putting it in a script.
For example if i need to find out how many files are in a directory rather than having a script i should write something like:
```
Count=0; for File in *; { [ -f "$File" ] && let Count++; } echo "$Count"
```
This neat little script reinforces a couple of functions that help make linux integration with bash so powerful. The use of a for loop and a simple test -f to find whether the item is a file are super useful commands.
