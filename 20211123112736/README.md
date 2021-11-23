# Pure bash implementation of the wc command with -w flag

We can emulate wc with the -w flag in bash with two lines of code removing the need to invoke wc in our script.

```bash
read -a String <<< 'This is a string with multiple words'
printf '%d\n' ${#String[@]}
```

