<img src="Cookies vs Tokens.assets/Screen Shot 2021-09-13 at 6.43.35 PM.png" alt="Screen Shot 2021-09-13 at 6.43.35 PM" style="zoom:50%;" />

# Cookie-Based Auth

cookie: a random piece of string created by browser. After that each time browser send request with this cookie, server will identify this browser

Stateful : authentication record or session must be kept both in the browser and server

browser keep cookie session in header, server has to keep track the cookie in the database

when logout, session will destroyed both on browser and server

# Token-Based Auth

instead of send back token, server will send back JWT to browser

token will be save in browser's local storage or session storage

Stateless: server doesn't save token, server can validate token (after decoding) without store them. 

## Pros

stateless (token is self-contained)

 less server work

token can contains more infomation in it( such as username etc.)

easy to work with different APIs (JWT cna be sent to different APIs)

can serve both browser and native mobile platforms.

## Cons

JWT are a lot bigger than cookie

it can be danger to save info into JWT since JWT can be stolen

# Resources

Cookie based authentication and token based authentication is a complex topic with a lot of opinions. It's always good to learn both sides and understand the pros and cons. I will leave these resources for you to explore, but keep in mind that it is better to come back to these after you have completed this section so you have a better understanding of how everything works. 

1. https://dzone.com/articles/cookies-vs-tokens-the-definitive-guide

2. https://stackoverflow.com/questions/17000835/token-authentication-vs-cookies

3. https://scotch.io/bar-talk/why-jwts-suck-as-session-tokens