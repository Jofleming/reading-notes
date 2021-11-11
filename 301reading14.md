# 301 Reading 14 - Authentication

## What is OAuth

Questions:
What is OAuth?
Secure, third-party, user-agent, delegated authorization.

Give an example of what using OAuth would look like.
When you go to log into a website and it offers opportunities to login using another sites/service's log on.

How does OAuth work? What are the steps that it takes to authenticate the user?


What is OpenID?
OpenID is about authentication. In a comment referenced in the reading "OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans."



## Authorization and Authentication flows

Questions:
What is the difference between authorization and authentication?


What is Authorization Code Flow?
It exchanges an authorization for a token. User is redirected to Auth0 server, user gives password, auth0 redirects back with authorization code good for one use, auth0 sends this code to auth0 auth server which verifies everything.

What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?
Same as the above flow but with a code-challenge in it as well which must be verified.

What is Implicit Flow with Form Post?
An alternative to Authorization Code Flow. It is intended for public clients, or apps unable to securely store client secrets.

What is Client Credentials Flow?
System authenticates and authorizes the app rather than a user.

What is Device Authorization Flow?
Wtih input-constrained devices, rather than authenticate directly, they have you go to a link on a computer or smartphone and authorize the device. This is to help users avoid the bad experience of trying to auth on devices that have no easy way to enter text.

What is Resource Owner Password Flow?
Highly trusted applications can use this flow, which requests that users provide credentials (username and password) using an interactive form.



[Back](README.md)