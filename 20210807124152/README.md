# How to save a file that required sudo

Just found this awesome tip for saving a file that needed sudo.
We can use `:w !sudo tee %`, which will ask for the sudo password and
save the file for you.

