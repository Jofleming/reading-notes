# Operators and Loops

## Operators

- Equal (==) : Returns 'true' if the operands are equal
- Not Equal (!=) : Returns 'true' if operands are not equal
- Strict Equal (===) : Returns 'true' if the operands are equal and of the same type
- Strict Not Equal (!==) : Returns 'true' if the operands are of the same type but not equal, or are of different types.
- Greater Than (>) : Returns 'true' if the left operand is greater than the right operand
- Greater Than or Equal (>=) : Returns 'true' if the left operand is greater than or equal to the right
- Less Than (<) : Returns 'true' if the left operand is less than the right
- Less Than or Equal (<=) : Returns 'true' if the left operand is less than or equal to the right.

### Arithmetic Operators

Along with the typical ones, useful ones are:
- Remainder (%) : Binary Op. Returns integer remainder of dividing two operands ` 12 % 5 returns 2 `
- Increment (++) : Unary op. ` ++x ` Will add one and then return. ` x++ ` will return x then add one.
- Decrement (--) : Unary op. Same as above but minus one.
- Unary negation (-) : Returns the negation of the operator
- Unary plus (+) : Unary Op. Attempts to conver the operand to a number if not already. ` +true comes back 1 `
- Exponentiation operator (**) : Calculates the base to the exponent power. Base^Exponent.





## Loops and Iteration

### For statement

A `for` loops repeats until a specified condition evals to false.

```
for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement
```

Below is the example Roger shared. This loop will continue increasing i and logging it up until the i = 12 is met.

```
for (let i = 0; i <=12; i = i +1){
    console.log(i);
}
```

When it is exectuted the initial expression is executed. This starts one or more loop counters.


### While Loop

```
let userAnswer = 10;

while(userAnswer < 20){
    userAnswer = prompt('Please enter a number greater than 19')
}
```

[Back](README.md)