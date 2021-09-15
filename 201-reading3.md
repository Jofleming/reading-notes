# Reading 3

## Chapter 3 Lists (pp. 62-73)

`<ol>` - Ordered List. Used to create a numbered list.
`<li>` - List Item. Used to wrap every item in any list.
`<ul>` - Unordered List. Used to create a list using bullet points.
`<dl>` - Definition List. Used to start a definition list.
`<dt>` - Definition Term. Used to contain the term being defined.
`<dd>` - Definition. Used to contain the definition. Generally indented.

You can put a second list inside of an `<li>`. This will make a nested list. A list indented even further.

```
<ul>
    <li>Text</li>
    <li>Text
        <ul>
            <li>More Text</li>
            <li>More Text</li>
        </ul>
    </li>
    <li>Last Text</li>
</ul>
```

## Chapter 13 Boxes (pp. 300-329)

Pixels are the typical way to adjust boxes as you can set the exact size.
Percents will resize the box relative to the page size.
With ems the size of the box is based on the size of the text within.
ems and percents are getting more popular as designers have to have multiple types of user devices in mind.

Display:
inline - Causes a block level element to appear inline.
block - causes an inline element to act like a block-level element.
inline-block - Causes a block-level element to flow like an inline element, while retaining other block level features.
none - This hides and element from the page. In this case, the element acts as though it is not on the page at all.

## JS Review Chapter 2 Basic JS Instructions (pp. 70-73)

Arrays stores a list of variables. You declare an Array like any other variable. Using var and then giving it a name. Values are assigned to it in [] brackets with each value separated by a comma. The values do not need to share a data type.

Can also use an 'Array Constructor'. This uses the command new Array() with the values in () instead of [] and still separated by commas.

Values in arrays are accessed as if they are in a numbered list that **STARTS AT 0**.

To retrieve an item in the array, the array name is specified along with the index number in square brackets. Below is an example of itemThree being declared and set to the third color from the colors array.

```
var itemThree;
itemThree = colors[2];
```

Arrays have a property called 'length' which holds the number of items in array. Below is an example of a variable being set to the length of an array.

```
var numColors;
numColors = colors.length;
```

Creating an array:

```
var colors = ['white',
    'black',
    'custom'];


```

## Chapter 4 Decisions and Loops (pp. 162-182)


[Back](README.md)