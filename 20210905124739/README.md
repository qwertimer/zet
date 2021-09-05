#  Bling strings with $

If you place a `$` outside the string in echo statements it will
expand the escape characters so if you need to show a tab in the echo
response you can use:
```
echo $'foo\tbar'
```
This will expand to `foo   bar` without the `$` symbol you would
need to use `-e`.

    #bash #escapechars

