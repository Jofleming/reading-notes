# React 3

## Nextjs

### Navigate Between Pages

[Reading](https://nextjs.org/learn/basics/create-nextjs-app)

In Next.js, a page is a React Component exported from a file in the pages directory.

Pages are associated with a route based on their file name. For example, in development:

* `pages/index.js` is associated with the `/` route.
* `pages/posts/first-post.js` is associated with the `/posts/first-post` route.

When linking between pages on websites, you use the `<a>` HTML tag.

In Next.js, you use the Link Component from next/link to wrap the `<a>` tag. `<Link>` allows you to do client-side navigation to a different page in the application.

#### Using Link

First, open `pages/index.js`, and import the Link component from next/link by adding this line at the top:

`import Link from 'next/link';`

Then find the h1 tag that looks like this:
```
<h1 className="title">
  Learn <a href="https://nextjs.org">Next.js!</a>
</h1>
```
And change it to:
```
<h1 className="title">
  Read{' '}
  <Link href="/posts/first-post">
    <a>this page!</a>
  </Link>
</h1>
```

Note: `{' '}` adds an empty space, which is used to divide text over multiple lines.

Link is more efficient than normal anchor tags since it uses client side navigation instead of forcing the browser to do the navigating and completely refresh.


## React Context for Beginners

[Reading](https://www.freecodecamp.org/news/react-context-for-beginners/)

React context allows us to pass down and use (consume) data in whatever component we need in our React app without using props.

In other words, React context allows us to share data (state) across our components more easily.

React context is great when you are passing data that can be used in any component in your application.

These types of data include:

* Theme data (like dark or light mode)
* User data (the currently authenticated user)
* Location-specific data (like user language or locale)

Data should be placed on React context that does not need to be updated often.

Why? Because context was not made as an entire state management system. It was made to make consuming data easier.

There are four steps to using React context:

1. Create context using the `createContext` method.
2. Take your created context and wrap the context provider around your component tree.
3. Put any `value` you like on your context provider using the value prop.
4. Read that value within any component by using the context consumer.

The created context is an object with two properties: `Provider` and `Consumer`, both of which are components. 

## Learn useContext in 13 Minutes

[Video](https://www.youtube.com/watch?v=5LrDIWkK_Bc)

Context is for passing down props to all of the children without having to manually pass in to every child. 


[Back](README.md)