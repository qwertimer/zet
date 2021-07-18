# Shell variables can be assigned and given a value inside a printf

It is quite simple to create a variable and give it a value directly inside a printf statement.
`printf -v Num '%02d' $Count` will create a shell variable named Num and assign it the value of count.

-- from Terminalforlife youtube, My shell Notes: Ep11
