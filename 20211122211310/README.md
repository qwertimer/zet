# Get wc using pure bash

To get the count of words in a file we can use bash's readarray function and the `#` sine in the array call along with the '@' to get the amount of words in a file:


```bash
readarray Lines < /etc/passwd
printf '%d\n' ${#Lines[@]}
```

To get the length of a string we can do:

```
read <<< "$USER"
printf '%d\n' ${#REPLY}
```


