# Reading 11 Assorted Topics

## Chapter 16 Images (pp.406-427)

You can specify the dimensions of images using CSS. It is common practice to set standard picture sizes, give them classes, and use them for multiple pages. If you set a picture
size with CSS first it will allow your page to render faster as it doesn't have to wait for it to load to set up the size of everything in relation.
Images can also be aligned both horizontally and veritcally. You can set background images behind box elements. You can also set the resolution, or put a screen behind the text to make it easier to read. You can create image rollover effects by moving background position of an image. You can also reduce the amount of images your browser has to load by using image sprites.

## Chapter 19 Practical Information (pp.476-492)

SEO or search engine optimization is what helps users find your site when using search engines. You can also use analtyics tools like Google Analytics to see how many users visit your site, how they found it, and then what they do when they get there. To actually get your site on the web you will need to obtain a domain name as well as web hosting. FTP programs (File Transfer Protocol) allow you to transfer your files from local computer to your web server.
- Note: Many companies provide platforms for blogging, e-mail newsletters, e-commerce, and other popular website tools. This saves you from writing them from scratch.


## Class Notes

### HTML Media + CSS Grid

HTML has native elements that let you display video, and play audio files.
    * Make sure your exenstions are audio / video extension.
    * Come with browser specific controls.
    * Media does NOT play automatically, unless you mute your audio.
        * Browsers force you to mute.
    * `controls` attribute must be included to let user control the audio/render it on the page.
    * `muted` attribute will start the player muted.
    * `autoplay` if it is muted you can have it autoplay. Generally used for video.
    * Make sure to close the tags.

```
<video src"path or URL .mp4" controls></video>

<audio src="path or URL .mp3" controls></audio>
```

### CSS Grid

A layout method, that works similar to flex, but while flex only lets you work in 1 dimension:
    * Take an HTML container, and tell it's children to be a `row` or a `column`.
    
CSS grid lets you specify 2 dimensions for your layout.
    * lets you define

For grid you have to set at least one row OR column. For the template you have to specify how much you want each to be seperated by a space:
```
div {
    display: grid;
    grid-template-columns: 100px
    grid-template-rows: 200px 200px
}

You can then control where things fall in the grid by targetting them. Lets assume we have something with an ID

#example {
    grid-start-column: 1
    grid-end column: 2
    grid-start-row: 1
    grid-end-row: 1
}
```
The above will give you ONE column of 100 pixels and TWO rows of 200 pixels. This works with all sizing units like view width and percent.


### Click Tracking



**Problem Domain:**
1. We need to present images to a user
2. The user needs to click on images to vote on a specific image.
3. We need to track based on image.
    * How many times is a specific image clicked.
4. We need to display a new image, after a click has been made.

How many images?

* Need something to keep track of all of our images.

What is an image:
    * Image ID (name)
    * number of clicks: starting at 0
    * URL: some image file to display
    * Is the image rendered.


[Back](README.md)