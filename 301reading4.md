# 301 Reading 4 - React and Forms

## React Docs - Forms

In HTML form elements normall maintain their own state based on user input. React has a mutable state kept in the state property of compounds. We can combine the two by making React state the only one. Then the React component that renders the form also controls what happens in it. This is what is called a controlled component.

### textarea Tag
In HTML a `<textarea>` element defines its text by its children. In React though the textarea uses a value attribute instead. This allows a form using this to be written very similarly to a form that uses a single-line input. You can set some state for you value (where you are expecting text) in the constructor to have some initial text appear in the form. (like "please type here")



Questions:
1. What is a ‘Controlled Component’?: One that normally has its own state, but we set to have the React function that renders it, control the state.

2. Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.

3. How do we target what the user is entering if we have an event handler on an input field?


## The Conditional (Ternary) Operator Explained

If statement syntax given:
```
if ( condition ) {
  value if true;
} else {
  value if false;
}
```

Ternary operator syntax given:
```
condition ? value if true : value if false
```

1. The condition is what you are testing. This should come out to true or false.
2. A ? separates the conditional from the **true** value. Anything inbetween the ? and the : is what is executed if the condition evaluates to true.
3. Finally a : colon. If condition is **false** then any code after this colon is executed.

Example given:
```
let person = {
  name: 'tony',
  age: 20,
  driver: null
};
person.driver = person.age >=16 ? 'Yes' : 'No';
```
Example given for multiple conditions:
```
let isStudent = false;
let isSenior = true;
let price = isStudent ? 8 : isSenior ? 6 : 10
console.log(price);
// 6
```


You can also set up for multiple operations. You must separate the operations with a comma. You also can but don't have to use parenthesis but it makes it look cleaner.

Example of multiple operations given:
```
let isStudent = true;
let price = 12;
isStudent ? (
  price = 8,
  alert('Please check for student ID')
) : (
  alert('Enjoy the movie')
);
```

Questions:
1. To simplify our code/make it easier to read. It replaces if statements.
2. Rewritten:
```
x === y ? console.log(true) : console.log(false);
```

## Things I want to know more about


[Back](README.md)