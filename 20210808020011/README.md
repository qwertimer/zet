# When using EOF line input use -.

If you want to wrap a large amount of text in something like a printf
statement rather than writing it all in one line use this:

```
while read -r; do
    printf '%b\n' "$REPLY"
done <<-EOF
    Here is some text
    and some more
    Would you like them apples
EOF
```
This makes the text so much more readable.

