# 401 Reading 6: Game of Greed 1

## How to use Random Module
[Reading](https://www.pythonforbeginners.com/random/how-to-use-the-random-module-in-python)

The random module provides access to functions that support many operations, including generating random numbers.

For random integers:
Randint:
```
import random
print random.randint(0, 10)
```
This will output a number between 1 and 10. The 0 is not included.


Random will random a number between .00 and 1. Multiply by 100 t0 make an integer.
```
import random
random.random() * 100
```

Choice will random a value from a squence such as a list.

```
import random
myList = [2, 109, False, 10, "Lorem", 482, "Ipsum"]
random.choice(myList)
```

Shuffle:
`random.shuffle(list)`
```
from random import shuffle
x = [[i] for i in range(10)]
shuffle(x)
```
Output:
* print x  gives  [[9], [2], [7], [0], [4], [5], [3], [1], [8], [6]]
(Results vary)

Randrange:
Will generate a randomly selected element from range(start, stop, step)
`random.randrange(start, stop[, step])`
```
import random
for i in range(3):
    print random.randrange(0, 101, 5)
```

Example from text.
```
Let’s see this example (copied from Doug Hellmann PYMOTW)

import random
import itertools

outcomes = { 'heads':0,
             'tails':0,
             }
sides = outcomes.keys()

for i in range(10000):
    outcomes[ random.choice(sides) ] += 1

print 'Heads:', outcomes['heads']
print 'Tails:', outcomes['tails']
There are only two outcomes allowed, so rather than use numbers and convert them, the words “heads” and “tails” are used with choice().

The results are tabulated in a dictionary using the outcome names as keys.

$ python random_choice.py

Heads: 4984
Tails: 5016
```

## What is Risk Analysis
[Reading](https://www.edureka.co/blog/risk-analysis-in-software-testing/)
Risk analysis is the process of identifying the risks in applications or software that you built and prioritizing them to test. After that, the process of assigning the level of risk is done.

Unavoidable risks:
1. The time that you allocated for testing

2. A defect leakage due to the complexity or size of the application

3. Urgency from the clients to deliver the project

4. Incomplete requirements


## Test Coverage
[Reading](https://martinfowler.com/bliki/TestCoverage.html)
You are doing enough testing if you rarely get bugs that escape into production AND you are rarely hesitant to change some code for fear it will cause production bugs.


## Big O Notation
[Video](https://www.youtube.com/watch?v=v4cd1O4zkGw)
The pigeon in the video is O(1) for time. The pigeon will always require the same time to fly. The data is O(n), that is the time it takes to transfer the data scales with how much data there is.
Important rules:
1. If you have different steps in your algorithm you add those steps.
2. Drop constants. O(2n) => O(n). You drop the 2.
3. Different inputs get different variables. Iterating through two different arrays is not O(n^2). It would be O(a*b)
4. Drop non-dominate terms. O(n+n^2) simplifies to O(n^2). The n^2 is dominate/affects the time more so you can drop the n+


[Back](README.md)