# Pythonisms

## Dunder Methods

[Reading](https://dbader.org/blog/python-dunder-methods)

* `__init__`: is the constructor for python classes. It takes care of setting up the object.
* `__repr__`: The “official” string representation of an object. This is how you would make an object of the class. The goal of `__repr__` is to be unambiguous.
* `__str__`: The “informal” or nicely printable string representation of an object. This is for the enduser.
* `__call__`: Can use this dunder to make an object callable. The downside is it can be hard to see what the point of calling the object would be. It is generally better to have explicit methods.
* `__enter__ , __exit__`: You can add context manager support using these two dunder methods and the with statement.
* `__len__`: For length, allows len() to be used
* `__getitem__`: Allows list slicing
* `__reversed__`: Allows iteration upon reversed order
* `__eq__`: Defines equality, allowing for `==`
* `__lt__`: Defines lesser-than, allowing for `<` and `>`
* `__add__`: Defines addition, allowing for `+`
* `__radd__`: Defines reverse addition, allows for addition across different types

## Iterators

[Reading](https://dbader.org/blog/python-iterators)

Objects that support the `__iter__` and `__next__` dunder methods automatically work with for-in loops.

Python offers these facades for other functionality as well. For example, `len(x)` is a shortcut for calling `x.__len__`. Similarly, calling `iter(x)` invokes `x.__iter__` and calling `next(x)` invokes `x.__next__`.

Iterators use exceptions to structure control flow. To signal the end of iteration, a Python iterator simply raises the built-in `StopIteration` exception.

Python iterators normally can’t be “reset”—once they’re exhausted they’re supposed to raise `StopIteration` every time `next()` is called on them. To iterate anew you’ll need to request a fresh iterator object with the `iter()` function.

## Generators

[Reading](https://dbader.org/blog/python-generators)

Generators are similar to regular functions, but they use `yield` instead of `return`. They can be used to write the iterator protocol is a nicer, more Pythonic manner.

Generator functions are syntactic sugar for writing objects that support the iterator protocol. Generators abstract away much of the boilerplate code needed when writing class-based iterators.

The yield statement allows you to temporarily suspend execution of a generator function and to pass back values from it.

Generators start raising StopIteration exceptions after control flow leaves the generator function by any means other than a yield statement.

```
def bounded_repeater(value, max_repeats):
    for i in range(max_repeats):
        yield value
```

[Back](README.md)