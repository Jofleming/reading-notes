# JavaScript Reading

JavaScript (JS) - a lightweight, interpreted, compiled programming language with first class functions. It is used in "functional programming" styles.

``` 
<html>
<head>
  <title>Hello World</title>
</head>
<body>
 
First name: <input id="first_name">
Last name: <input id="last_name">
<button id="say">Say hi!</button>
 
<hr>
<div id="result"></div>
 
<script>
function say_hi() {
    var fname = document.getElementById('first_name').value;
    var lname = document.getElementById('last_name').value;
 
    var html = 'Hello <b>' + fname + '</b> ' + lname;
 
    document.getElementById('result').innerHTML = html;
}
 
document.getElementById('say').addEventListener('click', say_hi);
</script>
 
</body>
</html> 
```

Above is an example of making a box to enter first name, last name, and a button to press.

In JS you can declare variables using
- `var`
- `let`
- `const`

## Variables

Variables are containers for storing data values. You can set variables to hold values, or plug into functions. I.E. price1 = 5 price2 = 6 and total = price1 + price2. All would be labled before with var
`var price1 = 5;`

## Identifiers

All JS variables must be indentified with unique names called identifiers.

- They can contain letters, digits, underscores, and dollar signs.
- Must **begin** with a letter, underscore, or $.
- Are case sensitive.
- And reserved words cannot be used as names. Such as JS keywords.

## Assignment Operator

In JS = is an assignment operator. The example given is ```x = x + 5```
This is nonsense in math but works in JS. It will calculate x + 5 and puts the results into x. The value of x is incremented by 5.

In JS the "equal to" operator is written as `==` instead.

JS can handle numbers like 100 and text values wrapped in "" like "hello".

When you declare a variable you then have to define it. You can do so separately or in the same line.

Separately:
``` var carName; 
carName = "Mustang";```

Same line:
``` var carName = "Mustang"; ```

You can then "output" the value inside a HTML paragraph. In the example using id="demo"

``` <p id="demo"></p>

<script>
var carName = "Mustang";
document.getElementById("demo").innerHTML = carName;
</script> ```

You can also declare/define many variables in one statement. This statement can be in one line or multiple.

The value of a variable does not have to be defined. It will come base as undefined. For example the value can be something that must be calculated or provided later by user input.

JS can also do arithmetic. Example given is:
`var x = 5 + 2 + 3;` and outputs 10 when it is retrieved in HTML. The same idea can be used with names as well.
`var x = "John" + " " + "Doe";` will output John Doe when retrieved. Two + and a "" with a space was added to keep from having the output be JohnDoe.

If you put a number in "" it will list any other numbers after as a chain with that number locked.
`var x = "5" + 2 + 3;` becomes 523 since 2 and 3 follow.
`var x = 2 + 3 + "5";` becomes 55 since 2 and 3 are added and then the list begins.



[Back](README.md)