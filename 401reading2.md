# 401 Reading 2 Testing and Modules

## In Tests We Trust
Unit tests are peices of code to exercise the input, output, and behavior of code. Test names are often much larger as they really explain what it is you are doing/testing. The file name should follow the module name more. Example in reading is, if module is gener.py the test should be test_gender.py. Tests should also be seperated from production code.

Arrange:
You need to organize the input, the data needed to execute.

Act:
Execute the code being tested or the behavior.

Assert:
After executing, check the result to make sure it is inline with what is expected.

Test should be ran without a method to make sure it fails, you can then write a method that just returns the correct answer to make sure the test can read an output correctly.


## If name equals Main
Notes taken directly from reading:
1. Every Python module has it’s __name__ defined and if this is ‘__main__’, it implies that the module is being run standalone by the user and we can do corresponding appropriate actions.

2. If you import this script as a module in another script, the __name__ is set to the name of the script/module.

3. Python files can act as either reusable modules, or as standalone programs.

4. if __name__ == “main”: is used to execute some code only if the file was run directly, and not imported.


## Recursion
Recursion is when a function calls itself directly. The video gives a great example using factorials. Where factorial of n is equal to n times factorial of n-1. This causes the program to call itself with what n-1 is, which requires n-2. This needs a stack to run. At the bottom factorial of 1 is 1 so it will go down recursively to one, then pass back one by one till it informs the first pending question.

The factorial of 1 example is an example of the base condition. A solution to the base case is provided, so no matter how "high up" you go, you can back down recursively to your base condition, and then solve your way back up.

A good way to think about it is your are breaking your much larger problem into a set of much smaller problems and solving them each one by one.

If you never reach your base case, a stack overflow will occur. Using the above idea. If you set your base at 50 but start your recursion under that, it will never reach 50.

There are direct and indrect recursive functions. Above, where the function calls itself, is an example of direct recursion. Indirect recursion would be if the function called a different function, which then calls it.


[Back](README.md)