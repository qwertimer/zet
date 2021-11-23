# Bash has sed like substitution capabilities built in

We can use `//` in a variable to get substitution capability. For example if we want to globally substitute parts of a username we can do this with

```
printf '%s\n' "${USER//er/a}"
```
This in my case will remove er from qwertimer and replace it with a giving me the username of qwertima. Extremely useful in many situations.

