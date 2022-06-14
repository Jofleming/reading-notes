# React 4

## Next.js - Dynamic Routes

[Reading](https://nextjs.org/learn/basics/dynamic-routes)

First, we’ll create a page called `[id].js` under pages/posts. Pages that begin with [ and end with ] are dynamic routes in Next.js.

Now, here’s what’s new: We’ll export an async function called `getStaticPaths` from this page. In this function, we need to return a list of possible values for id.

![Dynamic routes picture](./assets/how-to-dynamic-routes.png)

In the reading on their index.js they map over their items and make li's like below.
```
<li className={utilStyles.listItem} key={id}>
  <Link href={`/posts/${id}`}>
    <a>{title}</a>
  </Link>
  <br />
  <small className={utilStyles.lightText}>
    <Date dateString={date} />
  </small>
</li>
```

Like `getStaticProps`, `getStaticPaths` can fetch data from any data source. In our example, `getAllPostIds` (which is used by `getStaticPaths`) may fetch from an external API endpoint.

## Next.js Deployment

[Reading](https://nextjs.org/learn/basics/deploying-nextjs-app)

A workflow suggested is:

We’ve just gone through the workflow we call DPS: Develop, Preview, and Ship.

* Develop: We’ve written code in Next.js and used the Next.js development server running to take advantage of its hot reloading feature.
* Preview: We’ve pushed changes to a branch on GitHub, and Vercel created a preview deployment that’s available via a URL. We can share this preview URL with others for feedback. In addition to doing code reviews, you can do deployment previews.
* Ship: We’ve merged the pull request to main to ship to production.



## Next.js 10 is here

[Video]()



[Back](README.md)