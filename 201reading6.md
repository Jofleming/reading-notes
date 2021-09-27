# 201 Reading Notes 6: JS Object Literals, The DOM

## Articles

## Chapter 3 Object Literals (pp.100-105)

In an object, variables become known as properties, and functions become methods.
Properties comes in key value you pairs.

Literal notation:
```
var hotel {
    name: 'Quay'
    rooms: 20,
    booked: 25,

    checkAvailability: function() {
        return this.rooms - this.booked;
    }
}
```
The first three are examples of properties with the bottom being a method.

Accessing an object with dot notation:

```
var hotelName = hotel.name;
var roomsFree = hotel.checkAvailability();
```
The dot is called a member operator.
`object.property/method` is the default to access a property of an object or method.
You can also access using square brackets:
`var hotelName = hotel['name'];`

## Chapter 5 Document Object Model(pp.183-242)

The DOM is implemented by the browser. When a page is loaded by a browser it creates a DOM tree. The DOM tree is made of:
* The Document Node: The node at the top of the tree, it represents the entire page. When you access any of the other nodes you do it via the document node.

* Element Nodes: HTML elements describe the structre of an HTML page. After you select an Element you can access its attributes or text.

* Attribute Nodes: 

* Text Nodes: 

### Working with the DOM Tree

Accessing and updating the DOM tree involves two steps:
1. Locate the node that represents the element you want to work with.
2. Use its text content, child elements, and attributes.

Step 1: Access the elements
* Select an individual node
    * `getElementById()` Uses the value of an element's id attribute.
    * `querySelector()` Uses a CSS selector, and returns the first matching element.
* Select Multiple Elements (nodelists)
    * `getElementsByClassName()` Selects all elements that have a specific value for their class attribute
    * `getElementsByTagName()` Selects all elements that have the specified tag name.
    * `querySelectorAll()` Uses a CSS selector to select all matching elements.
* Traversing Between Element Nodes (you can move from one element node to a related node element)
    * `parentNode` Selects the parent of the current element node.
    * `previousSibling/nextSibling` Selects the previous or next sibling from the DOM tree.
    * `firstChild/lastChild` Select the first or last child of the current element.

Step 2: Work with those elements.
* Access/update text nodes
    * `nodeValue` This property lets you access or update contents of a text node
    1. Select the element node
    2. Use the correct property to select the text node
    3. Use the text node's only property (`nodeValue`) to get the text from the element.
* Work with HTML content.
    * `innerHTML` property allows access to child elements and text content.
    * `textContent` for just the text content
    * Several methods let you create new nodes, add nodes to a tree, and remove nodes:
        * `createElement()`
        * `createTextNode()`
        * `appendChild() / removeChild()`
* Access or update attribute values.
    * Here are some of the properties and methods you can use to work with attributes : className / id - lets you get or update the value of the class and id attributes
    * `hasAttribute()` - Checks if an attribute exists
    * `getAttribute()` - Gets the attributes value
    * `setAttribute` - Update the value
    * `removeAttribute()` - Removes an attribute


## Class Notes

### Objects and the DOM

What is an javascript "Object"?
    * An object is much like an array:
        * It is a data structure.
            * anything that can contain / model data.
            * key / value pair: {key: value}
                * `let array = ["jacob", 31];`
                * `let object = {"name": "Jacob", "age": 31};`
            * Keys are often referred to as 'properties' of an object.
        * What types of things can you store in an object?
            * Any data type can be placed within an object, functions take on a different name when stored in an object. They are called methods
```js
let person = {
    // We can define properties in quotes or without quotes.
    name: "Jacob",
    age: 31,
    speak: function() {
        console.log('Hello!, my name is: ' + this.name);
    },
}

// dot notation
person.name

// bracket notation
person["name"] // bracket notation uses values to refer to properties. Bracket notation requires quotes. You can set a variable to a string and put in the variable directly.
let property = "age";
person[property] // => 31

// You can also use the above trick for a method. You have to have the () after to run the method still. Otherwise it will just tell you it is a function.
let prop2 = "speak"
person[prop2]()

person.speak(); // => "Hello, my name is: ..."
```

Let's create a Pokemon.

```js
let pokemon = {
    name: 'Charizard',
    abilities: ["blaze", "flame-thrower"],
    speak: function() {
        console.log(this.name.toUpperCase()+"!!!");
    },
    listAbilities: function () {
        for (let i = 0; i < this.abilities.length; i++) {
            console.log(this.abilities[i]);
        }
    }
}

pokemon.name; // => Charizard
pokemon.speak() // => CHARIZARD!!!!
pokemon.listAbilities(); // => Outputs array of abilities.
```

* Contextual 'this'
    * Changes depending on where 'this' is used.
        * If just typed in the browser, `this` refers to the global `window` object.
        * If used in an object, it refers to that specific object.

## The Document Object Model

* A Global object (in the browser) that lets us developers modify the HTML `document`
    * This object has methods that let us perform some really powerful behaviors:
        * `document.createElement`
            * Creates a new HTML element that can be added to the document.
                * Created elements just exist in our JS runtime, in order to be rendered they need to be added to the `document`.
            * returns that element to our runtime context.
            * `let text = document.createElement('p')` Defining text as creating a p tag.
            * `text.innerHTML = '<span>Hello World</span>` Requires HTML tag and what is inside them.
            * `text.innerText = 'Hello World'` Putting text into the element we already created.
            * `document.append(text);`
            * `let parentElement = document.getElementById('ID sig you want')` Allows us to select a parent to append to.
            * `parentElement.appendChild(text);` Uses the above variable to select the parent, then appends whatever child is in it with our text variable we defined earlier.
            * `let multipleParents = document.getElementsByClassName('Given Class Name')`

### Math.random

`Math.random()` Will output a random number between 0 and 1
`Math.random() * 6` Will output a number between0 and 6 (not including 6) including decimals.
`Math.floor(Math.random() * 6)` Will chop off the decimals, rounding down. Will ouput numbers from 0 to 5 since it will never include 6 and always round down.

### Modeling the Problem Domain

Engineers get abstract problems that do not have straight lines, only requirements and constraints.
* Hey can you build me a robot that cooks your food?
    * What are the behaviors, and data, that is required to allow a robot to cook your food?
        * What food are you cooking?
        * How long are you cooking the food?
        * Can it be cooked longer / shorter depending on weight?

Robot:
    * cookTime
    * foodType
    * foodWeight
    * cook()


[Back](README.md)