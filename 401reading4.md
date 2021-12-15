# 401 Reading 4 - Topic

## Classes and Objects
[Reading](https://www.learnpython.org/en/Classes_and_Objects)
Objects are a encapsulation of variables and functions into a single entity. They get their variables and functions from classes.

Example from reading:
```
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")
```
Add `myobjectx = MyClass()` to make the MyClass class an object.

To access:
```
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()

myobjectx.variable
```
If we were to print the last line it would print the string "blah"

You can create multiple different objects that are of the same class. However they are independent copies of the variables and therefore can be changed separtely.

```
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()
myobjecty = MyClass()

myobjecty.variable = "yackity"

# Then print out both values
print(myobjectx.variable)
print(myobjecty.variable)
```

To access a function you would use the dot notation like you did for the variable.

The `__init__()` function, is a special function that is called when the class is being initiated. It's used for asigning values in a class.
Example:
```
class NumberHolder:

   def __init__(self, number):
       self.number = number

   def returnNumber(self):
       return self.number

var = NumberHolder(7)
print(var.returnNumber()) #Prints '7'
```

## Thinking Recursively
[Reading](https://realpython.com/python-thinking-recursively/)
All recursive functions share a common structure of two parts: Base Case and Recursive Case.
That is you will have a base that all problems "above" that will call on itself until it reaches that base and then solve upwards.

When dealing with recursive functions, keep in mind that each recursive call has its own execution context, so to maintain state during recursion you have to either:
* Thread the state through each recursive call so that the current state is part of the current call’s execution context
* Keep the state in global scope

Threaded Example:
```
def sum_recursive(current_number, accumulated_sum):
    # Base case
    # Return the final state
    if current_number == 11:
        return accumulated_sum

    # Recursive case
    # Thread the state through the recursive call
    else:
        return sum_recursive(current_number + 1, accumulated_sum + current_number)

sum_recursive(1, 0)
```

Global example:
```
# Global mutable state
current_number = 1
accumulated_sum = 0


def sum_recursive():
    global current_number
    global accumulated_sum
    # Base case
    if current_number == 11:
        return accumulated_sum
    # Recursive case
    else:
        accumulated_sum = accumulated_sum + current_number
        current_number = current_number + 1
        return sum_recursive()
```
A data structure is recursive if it can be deﬁned in terms of a smaller version of itself. A list is an example of a recursive data structure.

Fibonacci Example:
```
def fibonacci_recursive(n):
    print("Calculating F", "(", n, ")", sep="", end=", ")

    # Base case
    if n == 0:
        return 0
    elif n == 1:
        return 1

    # Recursive case
    else:
        return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)
```

## Pytest Fixtures and Coverage
[Reading](https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)



[Back](README.md)