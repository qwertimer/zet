# Fun things you can do in a jupyter notebook

Jupyter notebook has some interesting shell integration. It is common knowledge that you can use the ! command to run a shell command. This is not limited to running ls and cd etc but any shell command that is on your path is able to be run. For example all my shell scripts are able to be run like the one below. 
!htitle title
`# ----------------------------------- title ----------------------------------`

The benefits of this is that i can create scripts to do specific things for example working with repls on microcontrollers could be integrated into a standard python script using bash integration.

Further to this any python variable is able to be piped to bash using the `$<var>`, this could then be used to pipe code blocks to a snippet file or similar to nbdev piping explicit code to a file to create python files from within jupyter notebooks.

The possiblities of integrating with other programs and languages is quite useful.


