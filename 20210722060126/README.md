# Again vim integration with bash for the win

I was writing a command in the terminal to test some scripts. The script is below. I added piping to xclip. Then inside vim i used `!!xclip -o` to paste the output in line.
Integrating vim with terminal is shining through again. Very much loving this process.

`url=( stoprecord | curl -s -F 'f:1=<-' ix.io) | lynx http://ix.io/3tFn | xclip `

