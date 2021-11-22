# Replace grep with bash 

We can use bash to do a simple grep for a line. This saves us running grep for a simple check.

```bash
while read; do
  if [[ $REPLY =~ ^ichy ]]; then
    printf '%s\n' "$REPLY"
    break
  fi
done < /etc/passwd
```


