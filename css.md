# CSS

CSS is the style you see on a web page. It turns the HTML structure into something more appealing.

`h1 {
    color: red;
    font-size: 5em;
}`

Above is a sample of CSS syntax. It opens with a selector, which in this case is the h1. You then put what you want to do to the selector in `{}` brackets. What you want to do comes in the form of **property** and **value** pairs. That is what you want to change about it and how you are you changing it. The propert, or what you are changing, comes before the colon. The value or how is after ending in a semi colon.

HTML will reference an external style sheet. This is where the CSS will live and that way you can change the entire look of a site with just the one file. These can be written in any text editor but must be saved with a .css extension.

You can also use Internal CSS directly in the HTML code. This will be referenced inside by the `<stle>` element.

The last is inline CSS. It can be applied directly to a single element in a HTML line. `<p style="color:red;">This is a paragraph.</p>`
It appears directly after the element in the opening tag.

The last read style sheet is the one that will be used. This will be whichever is referenced first on the HTML sheet. Whatever is linked to last for that element will be what is used. The cascading order to look at is:
1. Inline Style (inside a html element)
2. External and Internal style sheets. (in the head section)
3. Browser Default

## Useful tips

To reference CSS sheet add `<link rel="stylesheet" href="style.css" type="text/css">`
to the head in your HTML under title.

Displays will normally be across the entire page. Can put nav buttons inline by `li{ display: inline}`

`padding` will affect the space between element and border

`margin` will space out elements from each other.

`text-align` center. Will center on middle instead of left.

`#section1` Will be the target element for a section

`.center` Will target the element for a class.

[Back](README.md)