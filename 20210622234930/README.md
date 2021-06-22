# f-strings have some neat features

In python, f-strings allow you to call the result of a variable inside the
string quotation as follows 
`print(f"This is my value = {value}")`
What is even cooler is the additional functionality added in python3.8.
The first of these is using :
`print(f"{num_value = }")` - This will grab the name of the variable and
automatically do similar to the first line. This is incredibly useful when
debugging. We can also do arbitrary maths inside the f string and view the
results. `{num_value % 2 = }`. The ! character can be used to convert the
result between alpha, repr and string outputs for debugging. One other really
call feature is automatic string formatting using the `:` in an f string.
For example:

We have calculated the current time with datetime.utcnow(). Then we print the
result in year month day format with:
`print(f'{now=:%Y-%m-%d}')`
We can also use the string formatting to getdecimal places using `:2f` for
example. These features are incredibly helpful for debugging and testing
purposes.



