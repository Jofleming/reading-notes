# 301 Reading 2 - Slate and Props

Mounting, Updating, and Unmounting are the three phases of the component lifecycle.

Mounting: When an *instance* of a component is being created and inserted into the DOM. Constructor, static getDerivedStateFromProps, render, componentDidMount, and UNSAFE_componentWillMount all occur in this order during mounting.

Updating: Anytime a component is updated or changes state it is rerendered. The order this happens is
static getDerivedStateFromProps, shouldComponentUpdate, reder, getSnapshotBeforeUpdate, componentDidUpdate, UNSAFE_componentWillUpdate, UNSAFE_componentWillRecieveProps

Unmounting: When a component is removed from the DOM. This is the final phase in the lifecycle and the only event is componentWillUnmount.

render() is the only required method in a class component. It examines this.props and this.state when called.

componentDidMount() is invoked immediately after a component is mounted. If you need to load anything using a network or initialize the DOM it should go in this method. Also a good place to set up any subscriptions but don't forget to unsub in componentWillUnmount(). setState() can be called here but use sparingly as it will rerender.

shouldComponentUpdate() React by default rerenders after every state change. Setting this to false allows you to prevent that. This allows you to optimize performance a bit. If this method returns false then UNSAFE_componentWillUpdate(), render(), and componentDidUpdate() will not be invoked.

getSnapshotBeforeUpdate() Another rarely used method that captures a picture of the DOM to check it before actually changing anything on the DOM.

componentDidUpdate() Useful for performing network requests after a change.

componentWillUnmount() Method that allows you to clean up the DOM and network requests/subscriptions

Questions:
1. Render happens first
2. First thing to happen is the mounting phase, starting with the constructor
3. Constructor -> render -> componentDidMount -> React Updates -> componentWillUnmount
4. Allows you to load anything using a network or initialize the DOM. Also allows to set up subscriptions.


## React State vs Props

Props are like arguments in a functions. When you make a component you set what props you will pass to it. 

State is something that happens inside a component. It can be manipulated and changed in our component

Questions:
1. Anything like you would pass as an argument into a function.
2. Props are passed into a component from outside while state happens inside
3. When the state changes.
4. Anything you want to change in your component. Examples given were counters or forms. 

## Things I want to know more about
How do you use state?
If you export the state into another component does it then become a prop?


[Back](README.md)