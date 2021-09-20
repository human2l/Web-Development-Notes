# Client Code

```js
saveAuthTokenInSession = (token) => {
	window.sessionStorage.setItem('token', token);
}
```

<img src="Client Session Management.assets/Screen Shot 2021-09-20 at 6.20.43 PM.png" alt="Screen Shot 2021-09-20 at 6.20.43 PM" style="zoom:50%;" />

<img src="Client Session Management.assets/Screen Shot 2021-09-20 at 6.26.52 PM.png" alt="Screen Shot 2021-09-20 at 6.26.52 PM" style="zoom:50%;" />

<img src="Client Session Management.assets/Screen Shot 2021-09-20 at 6.34.53 PM.png" alt="Screen Shot 2021-09-20 at 6.34.53 PM" style="zoom:50%;" />

<img src="Client Session Management.assets/Screen Shot 2021-09-20 at 6.39.14 PM.png" alt="Screen Shot 2021-09-20 at 6.39.14 PM" style="zoom:50%;" />

# LocalStorage vs SessionStorage

LocalStorage is permernant, SessionStorage will be cleared when close tab or browser

# Resource

### Bearer Token

For more information about Bearer Token:

Read #9 in this article: https://auth0.com/blog/ten-things-you-should-know-about-tokens-and-cookies/

And then read this: https://security.stackexchange.com/questions/108662/why-is-bearer-required-before-the-token-in-authorization-header-in-a-http-re
