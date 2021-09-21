# Reading 7 Object-Oriented Programming, HTML Tables

## Domain Modeling

Domain modeling is the process of creating a coneptual model in code for a specific problem. An entity that stores data in properties and encapsulates behaviors in methods is commonly referred to as an object-oriented model. If atriculated well it can verify and validate the understanding of a specific problem. Can be used as a communication tool between multiple teams.

To define the same properties between many objects you want to use a `constructor function`. Below is an example.
```
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail);
console.log(corgiFail);
```
The constructor function is defined using function expresson. The variable is declared, then assigned a function with two parameters. When it is called the data inside the parameters are stored into the given properties. Storing data within properties will allow any newly created object to access the data later.

This is object-oriented programming.
    * The `new` keyword instantiates (i.e. creates) an object.
    * The constructor function inistializes properties inside that object using the `this` variable.
    * The object is store in a variable for later use.

### To model the random nature of user behavior you can use random number generators.
```
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail.generateRandom(1, 5));
console.log(corgiFail.generateRandom(1, 5));
```

### Calculate Daily Likes:
```
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

EpicFailVideo.prototype.dailyLikes = function() {
  var viewers, percentage;

  viewers = this.generateRandom(10, 30) * this.epicRating;

  if (this.hasAnimals) {
    percentage = 0.75;
  } else {
    percentage = 0.40;
  }

  return Math.round(viewers * percentage);
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail.dailyLikes());
console.log(corgiFail.dailyLikes());
```

### Calculate Weekly Likes:
```
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

EpicFailVideo.prototype.dailyLikes = function() {
  var viewers, percentage;

  viewers = this.generateRandom(10, 30) * this.epicRating;

  if (this.hasAnimals) {
    percentage = 0.75;
  } else {
    percentage = 0.40;
  }

  return Math.round(viewers * percentage);
}

EpicFailVideo.prototype.weeklyLikes = function() {
  var total = 0;

  for (var i = 0; i < 7; i++) {
    total += this.dailyLikes();
  }

  return total;
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail.weeklyLikes());
console.log(corgiFail.weeklyLikes());
```




Tips:
1. When modeling a single entity that will have many instances, build self-contained objects with the same attributes and behaviors.
2. Model its attributes with a constructor function that defines and initializes properties.
3. Model its behaviors with small methods that focus on doing one job well.
4. Create instances using the `new` keyword followed by a call to a constructor function.
5. Store the newly created object in a variable so you can access its properties and methods from outside.
6. Use the `this` variable within methods so you can access the object's properties and methods from inside.


## Chapter 6 Tables (pp.126-145)

### Summary

The `<table>` element adds tables to a web page. It is drawn row by row. Each row is created using the `<tr>` element (table row). Inside each row are a number of cells. Each cell represented by `<td>` or `<th>` for the header. You can make cells of a table span more than one row of column using **rowspan** or **colspan** attributes. For long tables you can split the table into a `<thead>`, `<tbody>`, and `<tfoot>`

## Chapter 3 Functions, Methods, and Objects (pp.106-144)

The `new` keyword and the object constructor create a blank object. You can then add properties and methods to it.
```
<!-- This is the object constructor function. -->
var hotel = new Object();
<!-- Using dot notation you can add value to keys (properties) -->
hotel.name = `Quay`;
hotel.rooms = 40;
hotel.booked = 25; 
<!-- You can also add a method to a constructor -->
hotel.checkAvailability = function () {
    return this.rooms - this.booked;
}
```
To create an empty object you can use literal notation. `var hotel = {}` The curly brackets create an empty object.

To update the value of properties use dot notation or bracket notation. To delete a property use the `delete` keyword. `delete objectname.propertyname;`
To add use `objectname.propertyname = propertyvalue;` or `objectname['propertyname'] = 'propertyvalue';`
To clear the value of a property you can set it equal to a blank string.

You can also use a function as a template for creating objects.
```
fucntion Hotel (name, rooms, booked){
    this.name = name,
    this.rooms = rooms;
    this.booked = booked;
    this.checkAvailability = function(){
        return this.rooms - this.booked;
    }
}
```
The `this` keyword is used instead of the object name to indicate the property or method belongs to the object that *THIS* function creates. The name of a constructor function usually begins with a capital letter instead of a lowercase. It is supposed to help developers remember to use the `new` keyword when they create the object.

You create new **instances** of the object using the constructor function. The `new` keyword followed by the function creates a new object. The properties of each object are given as arguments to the function. Below is an example of making two objects for different hotels using the function.
```
var quayHotel = new Hotel('Quay', 40, 25);
var parkHotel = new Hotel('Park', 120, 77);
```
Note: The `+=` operator is used to add content to an existing variable.

You can store arrays in an object or objects in an array. To store an array in an object you set a key to reference, and then the entire array as the value. You can reference specific spots in the array using `object.key[index wanted]`

To store an object in an array you have to use literal notation. It will look like: `[{val1: 11, val2: ham, val 3: placeholder}, {ob2val1: 87, ob2val2: turkey, ob2val3}, etc]` To reference a certain value you would type `objectname[index number for that object].valuewithinthatobject;` or for above `objectname[2].ob2val12;`

An **Object Model** is a group of objects that represent related things from the real world that are used together to form a model of something larger.

Three groups of built in Objects:
- Browser Object Model: Creates a model of the browser tab/window
- Document Object Model: (DOM) Creates a model of the current web page
- Global JS Objects: Do not form a single model. Instead are individuals that represent different parts of JS language.

### Summary

Functions allow you to group a set of unrelated statments together for a single task. They can take parameters (info or data) and may return a value. An object is a series of variables and functions that represent something from the world around you. In an object variables are known as properties while functions are called methods of the object. Browsers have objects that represent both the browswer and the document loaded in it. Javascript also has several built in objects. Some of them are String, Number, Math, and Date. They offer functionality to help you write scripts. Arrays and objects can be used to create complex data sets and both can contain the other.


## Class Notes




[Back](README.md)