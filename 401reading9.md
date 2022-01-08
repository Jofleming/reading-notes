# 401 Reading 9: Game of Greed 4

## Dunder Methods
[Reading](https://dbader.org/blog/python-dunder-methods)

Dunder methods let you emulate the behavior of built-in types.

`__init__` is like the constructor for your class. This takes care of setting up the class object.

`__repr__`: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

`__str__`: The “informal” or nicely printable string representation of an object. This is for the enduser.

```
class Account:
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
```

If you don’t want to hardcode "Account" as the name for the class you can also use self.`__class__.__name__` to access it programmatically.

If you wanted to implement just one of these to-string methods on a Python class, make sure it’s`__repr__`.

Now I can query the object in various ways and always get a nice string representation:
```
>>> str(acc)
'Account of bob with starting amount: 10'

>>> print(acc)
"Account of bob with starting amount: 10"

>>> repr(acc)
"Account('bob', 10)"
```

In the example he defines a method to create fake transactions. Now to make the class iterable he:
```
class Account:
    # ... (see above)

    def __len__(self):
        return len(self._transactions)

    def __getitem__(self, position):
        return self._transactions[position]
```
which allows him to use:
```
>>> len(acc)
5

>>> for t in acc:
...    print(t)
20
-10
50
-20
30

>>> acc[1]
-10
```

To iterate over transactions in reversed order you can implement the `__reversed__` special method:
```
def __reversed__(self):
    return self[::-1]

>>> list(reversed(acc))
[30, -20, 50, -10, 20]
```

Let’s add them. To not have to implement all of the comparison dunder methods, I use the functools.total_ordering decorator which allows me to take a shortcut, only implementing `__eq__` and `__lt__`:
```
from functools import total_ordering

@total_ordering
class Account:
    # ... (see above)

    def __eq__(self, other):
        return self.balance == other.balance

    def __lt__(self, other):
        return self.balance < other.balance
```
```
>>> acc2 > acc
True

>>> acc2 < acc
False

>>> acc == acc2
False
```

Let’s implement `__add__` to be able to merge two accounts. The expected behavior would be to merge all attributes together: the owner name, as well as starting amounts and transactions. To do this we can benefit from the iteration support we implemented earlier:
```
def __add__(self, other):
    owner = '{}&{}'.format(self.owner, other.owner)
    start_amount = self.amount + other.amount
    acc = Account(owner, start_amount)
    for t in list(self) + list(other):
        acc.add_transaction(t)
    return acc
```

You can also make an object callable like a regular function by adding the `__call__` dunder method. The reading makes the call print out a nice report:
```
class Account:
    # ... (see above)

    def __call__(self):
        print('Start amount: {}'.format(self.amount))
        print('Transactions: ')
        for transaction in self:
            print(transaction)
        print('\nBalance: {}'.format(self.balance))
```

So when it is called you get:
```
>>> acc = Account('bob', 10)
>>> acc.add_transaction(20)
>>> acc.add_transaction(-10)
>>> acc.add_transaction(50)
>>> acc.add_transaction(-20)
>>> acc.add_transaction(30)

>>> acc()
Start amount: 10
Transactions:
20
-10
50
-20
30
Balance: 80
```

* Please keep in mind that this is just a toy example. A “real” account class probably wouldn’t print to the console when you use the function call syntax on one of its instances. In general, the downside of having a `__call__` method on your objects is that it can be hard to see what the purpose of calling the object is.

* Most of the time it’s therefore better to add an explicit method to the class. In this case it probably would’ve been more transparent to have a separate Account.print_statement() method.



## Satistics - Probability
[Reading](https://www.dataquest.io/blog/basic-statistics-in-python-probability/)

At the most basic level, probability seeks to answer the question, “What is the chance of an event happening?” An event is some outcome of interest. To calculate the chance of an event happening, we also need to consider all the other events that can occur. The quintessential representation of probability is the humble coin toss. In a coin toss the only events that can happen are:

Flipping a heads
Flipping a tails
These two events form the sample space, the set of all possible events that can happen. To calculate the probability of an event occurring, we count how many times are event of interest can occur (say flipping heads) and dividing it by the sample space.

Central Limit Theorem lets us know that the average of many trials means will approach the true mean

## Intro to Statistics
[Video](https://www.youtube.com/watch?v=MdHtK7CWpCQ&ab_channel=SirajRaval)

3 main takeaways:

1. Statistical features like bias, variance, and many others help us explore a dataset to gain valuable insights.

2. Probability distributions define the percent chance that some event will occur, and we can use them to understand the spread of data.

3. Bayesian statistics expresses probability as a degree of belief in an event which can change as new information is gathered rather than a fixed value based on frequency.

[Back](README.md)