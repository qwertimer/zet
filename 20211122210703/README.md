# Mimic cat in pure bash

Watching terminalforlife video he showed how you can mimic cat with pure bash.
```bash
while read; do
  printf '%s\n' "$REPLY"
  done < 'file'
```
Where 'file' is any file on the system. Useful method to reduce calls to other programs such as cat when you dont need to.

