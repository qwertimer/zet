# Deciphering robs filter function

Rob has a filter function that is used in his scripts. 
From what i can tell it allows the script to run multiple calls
recursively. I will need to think on this function some more.


The function is:

```
_filter(){
  (( $# > 0 )) && return 0
  while IFS= read -ra args; do
    "${FUNCNAME[1]}" "${args[@]}"
  done
}
```
Robs run through of the script is below.

if `args` greater than `0` just return. if you don't have an argument loop through standard input put into array 
`FUNCNAME[1]` calls the caller and passes the arguments into it. Uses recursive function call


