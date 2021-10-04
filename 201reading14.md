# 201 Reading 14 CSS Transforms, Transitions, and Animations

## CSS Transforms
The transform property allows elements to change shape by methods like rotating, skewing, and scaling the chosen element. The change can be made to be immediate, or based on user input. Similar to pseudo classes.

Example given:
```
css
transform: matrix(1.0, 2.0, 3.0, 4.0, 5.0, 6.0);
transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);
transform: perspective(17px);
transform: rotate(0.5turn);
transform: rotate3d(1, 2.0, 3.0, 10deg);
transform: rotateX(10deg);
transform: rotateY(10deg);
transform: rotateZ(10deg);
transform: translate(12px, 50%);
transform: translate3d(12px, 50%, 3em);
transform: translateX(2em);
transform: translateY(3in);
transform: translateZ(2px);
transform: scale(2, 0.5);
transform: scale3d(2.5, 1.2, 0.3);
transform: scaleX(2);
transform: scaleY(0.5);
transform: scaleZ(0.3);
transform: skew(30deg, 20deg);
transform: skewX(30deg);
transform: skewY(1.07rad);
```

Example on rotation from bottom right
```
html
<!--html-->
<div>Some Text</div>
```
```css
/*css*/
div {
transform-origin: bottom right;
transform: rotate(180deg);
}
```

## CSS Transitions

The transition property is used to make an element change with a specified duration, including zero. 
Can be used on color, margin, padding, visibility, etc.

Example given:
```
html
<style>
a {
  color: #fff;
  background-color: #333;
  transition: all 1s ease-out;
}
a:hover,
a:focus {
  color: #333;
  background-color: #fff;
}
</style>

<nav>
  <a href="#">Home</a>
  <a href="#">About</a>
  <a href="#">Contact Us</a>
  <a href="#">Links</a>
</nav>
```

## CSS Animations
Animation is used in creating more transitions.
It refers to:
animation-
* delay
* duration
* direction
* iteration-count
* fill-mode
* animation-name
* animation-play-state
* animation-timing-function

Example given:
```
html
<div class="view_port">
  <div class="polling_message">
    Listening for dispatches
  </div>
  <div class="cylon_eye"></div>
</div>

<style>
.polling_message {
  color: white;
  float: left;
  margin-right: 2%;
}
.view_port {
  background-color: black;
  height: 25px;
  width: 100%;
  overflow: hidden;
}
.cylon_eye {
  background-color: red;
  background-image: linear-gradient(to right,
      rgba(0, 0, 0, .9) 25%,
      rgba(0, 0, 0, .1) 50%,
      rgba(0, 0, 0, .9) 75%);
  color: white;
  height: 100%;
  width: 20%;
  -webkit-animation: 4s linear 0s infinite alternate move_eye;
          animation: 4s linear 0s infinite alternate move_eye;
}
@-webkit-keyframes move_eye { from { margin-left: -20%; } to { margin-left: 100%; }  }
        @keyframes move_eye { from { margin-left: -20%; } to { margin-left: 100%; }  }
</style>
```

[Back](README.md)