# Structure Web Pages with HTML

## Wireframing
A pen/paper or program sketch of what you want your website to look like. Make sure to research idea/practices for what type of site you are making. Even if you are reaching outside your domain to use elements they have. Things to research are business/user goals, personas using the site, use cases, and cool features you get from researching other sites.

Make sure to have a user flow mapped out. Know how many pages you need and where you want them to start.

### Key Principles
1. Clarity - Think of what your page is, what user can do there, and make sure it satisfies their needs. Really build on what your goal is for the user.
2. Confidence - The more clear/useable your site is, the more confidence users will have in it. 
3. Simplicity - The more clean and useable your site is the more users will enjoy it. 

## HTML Basics

HTML stands for HyperText Markup Language. It is the structure of a site. It uses tags to mark or clump things together. A HTML "element" consists of the opening tag, content, and a closing tag. They can also have attributes which contain extra information that you don't want to appear in the content.

An attribute should always have: A space between it and the element name, the attribute name followed by an equal sign, and the attribute value wrapped in quotation marks.

### HTML Anatomy

- `<!DOCTYPE html>` Is a required preamble. Used to mean something, now it just makes sure the doc behaves correctly.
- `<html></html>` The html element that wraps all content on the entire page
- `<head></head>` This element is a container for all the things you want to include on your HTML page that is not what you are showing to the page viewer's. Includes things like keywords or page description that you want to appear in search results. Also CSS to style our content, character set declarations, etc.
- `<meta charset="utf-8">` Sets doc to use UTF-8 which includes most characters from most written languages. No reason not to set this.
- `<title></title>` Title element. Sets up the title of your page. This is what appears on your browser tab/describes it when bookmarked.
`<body></body>` Body element. This containts **all** content that you want to show web users.

`<img src="img location" alt="Image desc text">` The image element will post an image in the page. The alt text is a description of the image for if it does not load or using a screen reader.

### Marking up Text
Useful commands for HTML elements:

Headings:
`<h1>` through `<h6>`

Paragraphs:
`<p></p>`

Lists:
`<ul></ul>` For unordered and `<ol></ol>` for ordered. Each item in the list is wrapped individually in a `<li></li>` element.

Links: `<a></a>` is the anchor element. It then requires a href attribute and the content is what the button appears as. in total it looks like `<a href="site url">Button Name</a>`


## Semantics

Semantics refers to the *meaning* of a piece of code. 



[Back](README.md)