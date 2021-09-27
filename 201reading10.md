# Reading 9 JS Debugging

## Chapter 10 Error Handling and Debugging

### Summary:
If you understand execution contexts stacks and their two stages, then you are more likely to find the error in your code.
Debugging is the process of finding errors and involves a process of deduction.
The console helps narrow down the area in which the error is located so you can try to find the exact error.
JavaScript has 7 different types of errors. Each creates its own error object, which can tell you its line number and gives a description of the error.
If you know that you may get an error, you can handle it using the **try**, **catch**, and **finally** statements. Use them to give your users helpful feedback.

## Class Notes

### JS Debugging

* 4 Types of JS errors
    1. Syntax Error: a typo, an improperly place semicolon, etc.
    2. Reference Error: when you try to reference a function or variable that doesn't exist or is outside of your current scope. (ex. Using let to define a variable inside a function and then trying to reference it outside)
    3. Type Error: When you are using the wrong type. Often a sign that we have some issue with our data types.
    4. Range Error: You are using an unacceptable numeric value. (ex. new Array(-1)).
* Call Stack
    * A data structure (of type: stack) that holds all the function invocation, while those functions are performing their jobs.
* Order of Execution
    * Our engine performs specific things when reading our JS files.
        1. Create some scope for all the JS code associated with that web page.
        2. Read all the commands
            * Create variable memory
            * Create function memory
                * Functions get "hoist"ed to the top of the file.
        3. Executes all the commands.
            * Invoking functions
            * Putting values into variables.


### CSS Grid



[Back](README.md)