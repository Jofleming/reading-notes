# 301 Reading 3 - Passing Functions as Props

## React Docs - Lists and Keys

Keys help React identify which items have changed, are added, or are removed. Most often you would use IDs from you data as keys. As a last resort you can use the item index as a key. This is not recommended as the order of items may change.

A good rule is that elements inside the `map()` call need keys.

Keys only have to be unique among siblings. You can use the same keys for two different arrays.

Keys serve as a hint to React but don't get passed to components. If the same value is needed in your component, then pass it explicitly as a prop with a different name.

JSX allows embedding any expression in curly braces.

Questions:
1. A new array
2. You will return the entire map() method inside curly brackets.
3. Key
4. To let React know somthing has been added, changed, or removed.

## The Spread Operator

Spread syntax is the use of ellipsis (...) to expand an interable object into the list of arguments.

The spread syntax sends an array as separate arguments. It is useful for:
- Copying an Array
- Concatenating or combining arrays
- Using Math functions
- Using an array as arguments
- Adding an item to a list
- Adding to state in React
- Combining objects
- Converting NodeList to an array

In all of the above the spread syntax is expanding some iterable object. This is usually an array but can be used on any iterable including a string.

Spread syntax will not work on older browsers. In that case `Function.prototype.apply()` will have the same effect.

Example given:
```
// Using Function.prototype.apply() instead of the spread operator
[1,3,5].min() // undefined
Math.min([1,3,5]) // NaN
Math.min().apply(null, [1,3,5]) // 1
Math.max().apply(null, [1,3,5]) // 5
```

The spread operator creates a new reference to its primitive values, copying them. That is to say if you use the spread operator on an array, and then it changes and introduces a bug, the spread operator will not be affected as it would if you had used a `variable = referenced array`. However the spread operator only makes a shallow copy, not a deep copy. Nested arrays can still cause bugs.

Questions:
1. The elipsis used to sperate an interable object into separate arguments.
2. Copy a array, cocatenate arrays, adding an item to a list, converting NodeList to an array.
3. 
```
array1 = [1, 2, 3]
array2 = [4, 5, 6]
arraytotal = [...array1, ...array2]
console.log(arraytotal) -> 1, 2, 3, 4, 5, 6
```
4. 
```
array1 = [1, 2, 3]
arraymore = [...array1, 4, 5]
```
5. 
```
const object1 = {placeholder1}
const object2 = {placeholder2}
const objectcombined = {...placeholder1, ...placeholder2}
```

## How to Pass Functions Between Components

Create the function that changes the state IN the parent/area the state will need to change. You can then pass it like any other prop.

Questions:
1. He writes the function he wants to pass through in the parent/where the state that needs to change is.
2. The increment function in the video is making a new array, iterating through it to match the name sent in from the click, incrementing the count with that name, outputting that value, and then changing the state to the new array.
3. You pass it down like a prop. In the video he went into the person object an put in `increment={this.increment}` Which gives the person object accesss to the prop `this.props.increment()`
4. Using the notation for a prop. In the video he used `this.props.increment()`. So using the increment method prop on this app (the child).

## Things I want to know more about.
I don't know what to ask but not sure I get the key thing very well.
I was following the spread syntax reading up till adding to state in React.

[Back](README.md)