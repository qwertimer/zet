# Instead of using cut, grep or awk to get things like UID

We can you pure bash to get things like UID from the passwd file with a simple while read loop with a comparison search. This way we don't need to invoke a subshell or anything else.


```bash
while IFS=':' read -a Line; do
  if [ "${Line[0]}" == 'qwertimer' ]; then
    printf '%d\n' ${Line[2]}
    break
  fi
done < /etc/passwd
```


