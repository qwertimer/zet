# Fun with colours in the terminal

We can do a lot with ANSI escape sequences in the terminal. These escape sequences are methods of changing how the terminal is shown including colourising, blinking, bold, underline and other things. To implement many of the colour changing and modifiers we use \e followed by [ and a number. To stop the modification we use \e[0. 

Some cool things we can do with this functionality is something like:
```
printf "\e[38;5;33m DANGER"
```
this will make a DANGER warning in red with it blinking. Not all terminals work with this. This is quite useful to modify your prompt. 

Other normal escape sequences include \n \r and so on. Further learning on this will be used to customise the prompt



