# Reading 8 Forms and JS Events

## Chapter 7 Forms (pp144.175)
`<form>` Holds all form controls. This element should carry the action attribute. Normally also having an ID and method.
`<action>` Every form element requires an action attribute. The value for it is the URL for the page on the server that will recieve the information in the submitted form.
`method` Forms can be set using one of two methods. `get` or `post`.
`get`
`post`

`<input>` The input element is used to create several different form controls. The value of the `type=` attribute determines what kind of input. (ex `<input typeof="">`)
`type="text"` When the type attri is text, it creates single line text input.
`name` Each form control requires a name attribute to explain to the server what type of data is being submitted.
`maxlength` Can use maxlength to limit the number of characters a user may enter into the field. (Ex could set to 4 when asking for a year)

`type="password"` When type is password it creates a single line text box, but this time the characters are blocked out. Like above it can take the name, size, and maxlength attributes.
`<textarea></textarea>` This isused to create a multi line text input. Unlike the others this is not an empty element and needs a closing tag. Any text inbetween them will appear in the text box when the screen loads. If the user does not delete this text, it will get sent to the server along with user input. You CAN use JS to auto clear it when clicked into.

`type="radio"` Radio buttons allow users to pick just one of a number of options.
`value` Value attribute indicates the value that is sent to the server for the selected option. The value for each button in a group should be different, so server knows which is selected.
`checked` The checked attribute can be used to indicate which value, if any, should be selected when the page loads. The value of this attribute is checked. Only one should have this value.

`type="checkbox"` Checkboxes allow users to select one or more options in answer to a question. This once again has the `name` , `value` , and `checked` attributes.

`<select></select>` A drop down list box, known as a select box. Allows users to select one option from a drop down list. It contains two or more `<option>` elements. This also has the value and selected attributes.
`<option></option>` Used to specify the options a user can select from. The words between will be shown to the user.
Note: This works similarly to the radio buttons. Use radio if you need them to see all options at once. Use select for longer lists.
`size` You can turn a drop down select box into a box that shows more than one option by adding the size attribute. The value of which is how many you want to show at once. However it is browser dependant and doesn't work as well on Safari or Firefox.
`multiple` You can allow users to select multiple options from this list by adding the multiple attribute with the value of multiple. It is good practice to let the user know they can select multiple. And that on windows they should hold down control while selecting multiple, and command key on mac.


### Summary
Whenever you want to collect information from visitors you will need a form, which like one might expect, lives in the `<form>` element.
Information from a form is sent in name/value pairs.
Each form control is given a name, and the text the user types in or the values of the options they select are sent to the server.
HTML5 has new form elements which makes it easier for the user to use forms.

## Chapter 14 Lists, Tables, and Forms (pp.330-357)

### Summary
In addition to the CSS properties which work with the contents of all elements, several others are specifically used for list, tables, and forms appearence.
List markers can be changed using `list-style-type` and `list-style image` properties.
Table cells can have different borders and spacing in different browsers. But there are properties you can use to make them more consistent.
Forms are easier to use if the form controls are vertically aligned using CSS
Forms benefit from styles that make them feel more interactive.

## Chapter 6 Events (pp.243-292)

### Summary
Browers indicate something has happened with **events**, like when a page loaded or button has been clicked. **Binding** is the processs of stating which event you are waiting to happen, and which element you are waiting for that to happen upon. When an event occurs on a given element, it can trigger a JS function. This is used to make the page feel responsive to the user. This is done by make the page change in some way using the function when the user does something. You can use event delegation to monitor for events that happen on all of the children of an element. The most commonly use events are W3C DOM events, although HTML5 has others, as well as browser specific events.


## Class Notes

### HTML Forms

**Elements that handle user input.**

* Buttons: Clickable element that "does form things"
* Input: generic text input elements.
    * type attribute sets the type of value that the input recieves
* Field Sets: a group of inputs.
* Legends: A title/label for the fieldset/group of inputs
* Form: A 'container' element for all inputs that belong to a shared event.

`<fieldset></fieldset` Sets the field for a form
`<legend></legend>` Give the field a title.
`<label></label>` Gives a label text box. Used to put next to a input field
`<button></button>` Makes a button with whatever text you have in between tags on it.
`required` will give a notification if field is empty

### Browser Events

Our functions are going to be invoked, not explicitly in our code, but by the browser when something happens.
* We have to define parameters: `function (param) {}` , that we didn't create ourself.

* What events are there?
    * When mouse moves
    * when you click on anything.
        * Right click and left click.
    * When you hover over things.
* All of these events are associated with some element / object in the Browser. We access with the DOM.
* We tap into this by using a method on an element: `addEventListener`
    * We pass a function into this method, that will run when a specific event happens.

[Back](README.md)