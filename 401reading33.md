# Authentication and Production Server

## JSON Web Tokens

[Reading](https://jwt.io/introduction/)

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

Here are some scenarios where JSON Web Tokens are useful:

* Authorization: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.

* Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:

* Header
* Payload
* Signature
Therefore, a JWT typically looks like the following.

xxxxx.yyyyy.zzzzz

The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

Example:
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```

For practice go to `https://jwt.io/#debugger-io`

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

`Authorization: Bearer <token>`

Let's talk about the benefits of JSON Web Tokens (JWT) when compared to Simple Web Tokens (SWT) and Security Assertion Markup Language Tokens (SAML).

As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.

## DRF JWT Authentication

[Reading](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)

The JWT is acquired by exchanging an username + password for an access token and an refresh token.

The access token is usually short-lived (expires in 5 min or so, can be customized though).

The refresh token lives a little bit longer (expires in 24 hours, also customizable). It is comparable to an authentication session. After it expires, you need a full login with username + password again.

The signature is issued by the JWT backend, using the header base64 + payload base64 + `SECRET_KEY`. Upon each request this signature is verified. If any information in the header or in the payload was changed by the client it will invalidate the signature. The only way of checking and validating the signature is by using your application’s `SECRET_KEY`. Among other things, that’s why you should always keep your `SECRET_KEY` secret!

## Django Runserver is Not Your Production Server

[Reading](https://vsupalov.com/django-runserver-in-production/)

## JWT with DRF

[Video](https://www.youtube.com/watch?v=Fhcn2qx-4VQ)

JSON Web tokens are a way to verify information without using a database. If you have the secret when generating the token then you can validate if anybody sends you that same token back. 


[Back](README.md)