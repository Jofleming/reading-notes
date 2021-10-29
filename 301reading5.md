# 301 Reading 5 - Putting it all together

## React Docs - Thinking in React

The `single responsibility principle` states that a component should ideally only do one thing.

Good practice is to make a component map for your project. Each component should take on one task. After you identify them you should arrange them into a hierarchy. Components that appear within another component in your mock should be a child in your hierarchy.

Next you should build a static version. That is one with no interactiviy. Making components that pass data using props is great. But do not use state in this version as that is all about interactivity. With smaller projects it is easier to code top-down, and with larger projects it is easier to code bottom-up and write tests as you build.

At the end you will have a library of components. You will only have `render()` methods since it is a static version. To test you can make changes to your underlying data and call `ReactDOM.render()`

To check if something is state as three questions:
1. Is it passed in from a parent via props? If so, not state.
2. Does it remain unchanged over time? If so, not state.
3. Can you comput it based on any other state or props in your component? If so, not state.

After determining what is state you need to determine which component mutates or "owns" this state.

Useful steps to figure out who owns the state taken from 'https://reactjs.org/docs/thinking-in-react.html':
* Identify every component that renders something based on that state.
* Find a common owner component (a single component above all the components that need the state in the hierarchy).
* Either the common owner or another component higher up in the hierarchy should own the state.
* If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

Then write a callback function to change state and pass it down to the child components that need it.


Questions:
1. It is that a function, object, or in this case a component should only do one thing.
2. Build one with no interactivity. Get the major amount of typing done before worrying about adding the code to make it interactive.
3. After you have your static it is time to add state to allow interactivity.
4. * Is it passed in from a parent via props? If so, not state.
   * Does it remain unchanged over time? If so, not state.
   * Can you comput it based on any other state or props in your component? If so, not state.
5. Determine the highest up component in the hierarchy that directly owns a component that needs state. That is the common owner or one higher.

## Higher-Order Functions

Functions that operate on other functions, either by taking them as arguments or returning them are higher order functions.

Cool function in the reading:
```
fucntion unless(test, then) {
    if (!test) then ();
}

// Example of above skeleton in practice.
repeat(3, n => {
    unless(n % 2 == 1, () => {
        console.log(n, "is even");
    });
});
// -> 0 is even
// -> 2 is even
```

Questions:
1. Functions that operate on other functions, either by taking them as arguments or returning them are higher order functions.
2. 
3. 

## Things I want to know more about.



[Back](README.md)