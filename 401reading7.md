# 401 Reading 7 - Game of Greed 2

## Python Scope
[Reading](https://realpython.com/python-scope-legb-rule/)

The concept of scope rules how variables and names are looked up in your code, or the visibility of the variable. The scope is determined
by where the name or variable is created in your code.

Python scope is presented as LEGB rule.
This stands for: Local, Enclosing, Global, and Built-in.

This also summarizes the squence of steps Python follows when resolving names.

Understanding Scope:
The scope of a name defines the area of a program in which you can unambigously access that name, such as variables, functions, objects, and so on. A name
will only be visible and accessible by the code in its scope. 

Most commonly you will be dealing with global scope and local scope.

Global Scope: The names that you define in this scope are available to all code.

Local Scope: The names that you define in this scope are only available or visible to the code within the scope.

### Global Statement

A global statement lets you define a list of names that are going to be treated as global names. The statement consists of the global keyword, followed by one ore more names
separated by commas.

```
counter = 0  # A global name
def update_counter():
    global counter  # Declare counter as global
    counter = counter + 1  # Successfully update the counter

update_counter()
counter

update_counter()
counter

update_counter()
counter
```

The above will allow you to modify the global variable within the local scope of the function.
Using global to solve your problems is considered bad practice.

### Non-local Statement

Non local names can be accessed from inner functions but not assigned or updated without using a non local statement. The statement consists of the nonlocal keyword followed by one ore
more names separated by commas. However, different from global, nonlocal statements cannot be used in the global or local scope. It can only be used in a nested function.

## Don't be CONFUSED by BIG O notation anymore!
[Video](https://www.youtube.com/watch?v=5Uqawfl0VHQ)

Big O tries to explain how long it takes an algorithm to do something, and how much memory it takes to do it.
Common types:
O(1) - Constant running time
O(log n) - Logarithmic running time
O(n) - Linear Running time
O(n log n) log-linear running time
O(n^k) Polynomial running time
O(c^n) - Exponential running time

[Back](README.md)