# Class 2 Reading

## Chapter 2 Text (pp. 40-61)

This chapter begins on explaining tags to use to manipulate script.

`<sup> </sup>` is introduced. This marks text as a superscript.
`<sub> </sub>` is also introduced. This marks text as a subscript.

For white space, the browser will read any amount of spaces directly next to each other as one space. It will also do this with a line break. It is called white space collapsing. If you want a break to appear in a certain spot you have to use a new command:

`<br />` - This will add a break in a line when loaded on a page. You can keep typing in line in the actual code.
`<hr />` - This will add a horizontal line across the page. Must sit on its own line in code.

Both of the above are called empty elements. They contain the element and the closing all in one bracket.

`<blockquote> </blockquote>` - This will indent any text in it and make it free floating. Used for longer quotes. You can also cite your sourch in the main tag `<blockquote cite="URL">`
`<q> </q>` - is used for inline quotes. You can also cite in the opening tag.

`<abbr> </abbr>` - Is used for abbreviations. Put the full unabbreviated version in the opening tag so you can see if you mouse over on the actual page. `<abbr title="Non Abbreviated Version">`

`<cite> </cite>` - Used when citing books. Will make it italic.
`<dfn> </dfn>` - Is often used when defining a new term.
`<address> </address>` - Is used to contain contact information. Most browsers will make it italic.
`<ins> </ins>` - Will underline the words. Used to show words inserted into a document.
`<del> </del>` - Will strike a line through the words. Used to show words deleted from a document.
`<s> </s>` - Will strike a line through the text as well. Used to show something is no longer accurate or relevant but that should not be deleted. `<u>` Used to be used to underline but is being phased out.


## Chapter 10 Introducing CSS (pp.226-245)
CSS treats each HTML **element** as if it was sitting inside its own box. It uses rules to indicate how that element should work. Rules are made up of selectors that specify which elements, and declarations that indicate what those elements should look like. Declarations are made of two parts: property that you want to change, and the value of said property.

```
element selector{
    what you are changing: how you are changing it;
}
```
The selector idicates what element(s) you are targeting in your HTML. You can select multiple elements at one time by separating them with a comma. You then on one line specifiy what you are changing about it or the **property** (text type, text color, background color, etc). After the colon you type the **value** you are assigning that (Arial, blue, red, etc).

To reference a CSS sheet in the `<head>` of a site use `<link href="css/styles.css" type="text/css" rel="stylesheet" />` This is an empty element so it doesn't need a closing tag. href specifies the **path** to the CSS file. Type says what type the document is. rel specifies the relationship between the HTML page and the file. The HTML page can use more than one style sheet.

You can also use `<style> </style>` for in line CSS styling. Make sure to add `type="text/css"` in the opening bracket.

CSS selectors are case sensitive:
`*` - Universal selector. Targets all elements
`h1, p, body` - Type selector. Targets types of elements
`.(class element)` - Class selector. Targets all elements with a class listed after the period.
`#(id attribute)` - ID selector. Targets all elements whose ID value is listed after the hashtag.
`element>element2` - Child selector. Targets any element 2 that are childen of element 1 but not any other.
`element element2` - Descendant selector. Targets any element2s that sit inside element1 even if other elements are nested between them.
`element1+element2` - Adjacent Sibling selector. Targets the first element2 after any element1. (But not other element2s)
`element1~element2` - General Sibling selector. If you had two element2s that are siblings to element1, this rule would apply to both.

### Cascading
In CSS the **Last Rule** applies. That last listed style is the one that will be applied. Along with the the most **Specific** rule will take precedence. You can also add `!important` after any <u>property</u> value to make it more important than other rules.

Font-family or color property values are inherited by child elements. If you set something for the `<body>` then everything contained within it will also have that applied. This is not the case for things like background color. You can however force child elements to inherit values by setting a rule with `inherit` **as** the CSS value.



## Chapter 2 Basic JavaScript Instructions (pp.53-84)



## Chapter 4 Decisions and Loops (pp.145-162)



[Back](README.md)