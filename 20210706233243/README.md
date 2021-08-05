# Bash has dictionaries, or associative arrays

[bash]
[vim]

we can make dictionaries in bash with `arr[key]=value`
We access the keys with !arr and values with `arr[@]`

An example that is really cool


### emoji filter
```
while read -r line; do
  for k in ${!emoji[@]}; do
    line=${line//:$k:/${emoji[$k]}}
  done
  echo "$line"
done
```
To access it in command line  
`echo 'some :smile: here and :pomo: there | toemoji`

To extend on this to be used in vim as an autocmd, we can create a autocmd with a vimleavepre.
BufWritePost will run the au command on save. We can use this with explicit file location to update a file that is only in a certain location.



  `
