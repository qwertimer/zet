# Mimic cut in pure bash

Watching terminalforlife video <https://www.youtube.com/watch?v=UwlbOGn0cW4>. He shoed that you can replace cut with a while read loop.
To do so you ned to change the `IFS` to which ever delimiter you want to cut on. For example inthe video he read the passwd file in which is delimited by :.

```bash
while IFS=':' read -a Line; do
  printf '%s\n' "${Line[2]}"
done < /etc/passwd
```
The code above reads into an array the lines from passwd. Then based on the value in {} displays that column. 
