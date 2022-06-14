# React 1

## Readings and Videos

[ES6 Syntax and Feature Overview](https://www.taniarascia.com/es6-syntax-and-feature-overview/)
[React - Hello World](https://reactjs.org/docs/hello-world.html)
[React - JSX](https://reactjs.org/docs/introducing-jsx.html)
[React - Rendering Elements](https://reactjs.org/docs/rendering-elements.html)
[React - Components & Props](https://reactjs.org/docs/components-and-props.html)
[React - State & Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
[React - Handling Events](https://reactjs.org/docs/handling-events.html)
[Utility First CSS](https://tailwindcss.com/docs/utility-first)
[Tailwind in 15 minutes](https://www.youtube.com/watch?v=6zIuAyLZPH0)
[Learn Next.js](https://nextjs.org/learn/basics/create-nextjs-app)
[Why to use Next.js](https://www.youtube.com/watch?v=rtgbaKBhdkk)

## ES6

`var` is Function scope, it allows Hoisting, it can be reassigned, and it can be redeclared.
`let` is Block scope, does not allow hoisting, can be reassigned, and cannot be redeclared.
`const`	is Block scope, does not allow hoisting, and cannot be reassigned or redeclared.

The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own `this`, do not have prototypes, cannot be used for constructors, and should not be used as object methods.

```
let func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple parameters
```

Expressions can be embedded in template literal strings.
`let str = "Release Date: ${date}"`

Using template literal syntax, a JavaScript string can span multiple lines without the need for concatenation.
Note: Whitespace is preserved in multi-line template literals.

The `return` keyword is implied and can be omitted if using arrow functions without a block body.
`let func = (a, b, c) => a + b + c // curly brackets must be omitted`

The `function` keyword can be omitted when assigning methods on an object.

```
let obj = {
  a(c, d) {},
  b(e, f) {},
}
obj.a() // call method a
```

Use curly brackets to assign properties of an object to their own variable.
```
var obj = {a: 1, b: 2, c: 3}

let {a, b, c} = obj
```

A more concise syntax has been introduced for iteration through arrays and other iterable objects.
```
for (let i of arr) {
  console.log(i)
}
```

Spread syntax can be used to expand an array.

```
let arr1 = [1, 2, 3]
let arr2 = ['a', 'b', 'c']
let arr3 = [...arr1, ...arr2]

console.log(arr3) // [1, 2, 3, "a", "b", "c"]
```

```
let arr1 = [1, 2, 3]
let func = (a, b, c) => a + b + c

console.log(func(...arr1)) // 6
```

The `extends` keyword creates a subclass.

Modules can be created to export and import code between files.

```
index.html
<script src="export.js"></script>
<script type="module" src="import.js"></script>
```

```
let func = (a) => a + a
let obj = {}
let x = 0

export {func, obj, x}


import.js
import {func, obj, x} from './export.js'

console.log(func(3), obj, x)
```

## React.js Hello World

Warning:
Since JSX is closer to JavaScript than to HTML, React DOM uses camelCase property naming convention instead of HTML attribute names.

For example, class becomes className in JSX, and tabindex becomes tabIndex.

## Components and Props

When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props”.

For example, this code renders “Hello, Sara” on the page:

```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
const element = <Welcome name="Sara" />;
root.render(element);
```

Let’s recap what happens in this example:

We call `root.render()` with the `<Welcome name="Sara" />` element.
React calls the Welcome component with {name: 'Sara'} as the props.
Our Welcome component returns a `<h1>Hello, Sara</h1>` element as the result.
React DOM efficiently updates the DOM to match `<h1>Hello, Sara</h1>`.

Note: Always start component names with a capital letter.

React treats components starting with lowercase letters as DOM tags. For example, `<div />` represents an HTML div tag, but `<Welcome />` represents a component and requires Welcome to be in scope.

### Converting a Function to a Class

You can convert a function component to a class in five steps:

1. Create an ES6 class, with the same name, that extends `React.Component`.
2. Add a single empty method to it called `render()`.
3. Move the body of the function into the `render()` method.
4. Replace props with this.props in the `render()` body.
5. Delete the remaining empty function declaration.

[Back](README.md)