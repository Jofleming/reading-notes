# 301 Reading 12 - CRUD

## Status Codes Based on REST Methods

Questions:
1. In your own words, describe what each group of status code represents:
    100’s = That everything is so far okay.
    200’s = Success codes for requests.
    300’s = Redirection codes. Tells client what they are requesting has moved.
    400’s = Client error codes. Client has sent an invalid request.
    500’s = Server error codes. Something on the server end went wrong.
2. What is a status code 202?
    * 202 is Accepted, often used in asynch processing.
3. What is a status code 308?
    * 308 is Permanent Redirect. Tells client to use different URL to access.
4. What code would you use if an update didn’t return data to a client?
    * You would use code 204 No Content.
5. What code would you use if a resource used to exist but no longer does?
    * 410 Gone
6. What is the ‘Forbidden’ status code?
    * Says the client has/doesn't need to authorize itself, but has no perms to access the resource.


## Build A REST API With Node.js, Express, & MongoDB - Quick

Questions:
Why do we need to pull our MongoDB database string out of our server and put it into our .env?
* So that when we are not using localhost it will update. We put in that path as a variable wherever our server is being hosted.

What is middleware?
* Code that runs when the server gets a request but before it gets passed to your routes.

What does app.use(express.json()) do?
* Lets our server accept json as a body instead of a post/git element.

What does the /:id mean in a route?
* It is a parameter that we can access.

What is the difference beween PUT and PATCH?
* PUT replaces all of the information of whatever you are changing, PATCH replaces only what you are passing in.

How do you make a defalut value in a schema?
* `default: element.now` in the video element is 'Date'.

What does a 500 error status code mean?
* Means there is an error on the server. Tells them it had nothing to do with the client.

What is the difference between a status 200 and a status 201?
* 201 is more specific. 200 says everything was successful while 201 says that you successfully created something. 201 is better for a POST route.



[Back](README.md)