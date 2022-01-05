# 401 Reading 8: Game of Greed 3

## List Comprehensions
[Reading](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python)

3 things are needed for a python list taken directly from reading:
1. First is the expression we’d like to carry out. expression inside the square brackets.
2. Second is the object that the expression will work on. item inside the square brackets.
3. Finally, we need an iterable list of objects to build our new list from. list inside the square brackets.

You can also created a list using a range()
```
# construct a basic list using range() and list comprehensions
# syntax
# [ expression for item in list ]
digits = [x for x in range(10)]

print(digits)
```

You can also do it with a standard for loop:
```
# create a list using a for loop
squares = []

for x in range(10):
    # raise x to the power of 2
    squares.append(x**2)

print(squares)
```

You can sort a list for digits only.
```
# user data entered as name and phone number
user_data = "Elvis Presley 987-654-3210"
phone_number = [ x for x in user_data if x.isdigit()]

print(phone_number)
```

Change the cases of letters in the list:
```
lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]

print(lower_case, upper_case)
```

[Back](README.md)