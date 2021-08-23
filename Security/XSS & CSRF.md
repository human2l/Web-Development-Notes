# Cross Site Scripting

## Session Hijacking

After inject the code below:

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 2.51.13 PM.png" alt="Screen Shot 2021-08-23 at 2.51.13 PM" style="zoom:50%;" />

window.location redirect the current page to the hacker's page, and sent user's data (i.e. login information in cookie) on current website to the hacker's website. Then hacker can use the user's data to login as user.

**Solution for this part: Sanitize input**

# Cross Site Request Forgery

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.01.29 PM.png" alt="Screen Shot 2021-08-23 at 3.01.29 PM" style="zoom:50%;" />

The link below can be sent by email or injected into some website:

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.03.19 PM.png" alt="Screen Shot 2021-08-23 at 3.03.19 PM" style="zoom:50%;" />

After a victim visits this webpage and the victim have already login to the "netbank.com", he will send $100 to Attacker because of the parameter of the link.

## How twitter prevent this

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.11.05 PM.png" alt="Screen Shot 2021-08-23 at 3.11.05 PM" style="zoom:50%;" />

### How to add "Content Security Policy":

```js
//Example if we are using express server
app.get('/', (req,res) => {
	res.set({
		'Content-Security-Policy': "script-src 'self' 'https://apis.google.com'"
	})
	res.send("Hello World!")
})
```

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.15.26 PM.png" alt="Screen Shot 2021-08-23 at 3.15.26 PM" style="zoom:50%;" />

```js
//Example if we are using express server
app.get('/', (req,res) => {
  res.cookie('session', '1', {httpOnly: true})
  res.cookie('session', '1', {secure: true})
	res.set({
		'Content-Security-Policy': "script-src 'self' 'https://apis.google.com'"
	})
	res.send("Hello World!")
})
```

HTTPOnly attribute prevents the cookies from being accessed by client side scripting,

Secure attribute makes sure cookie will be sent over the HTTPS connection.

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.20.08 PM.png" alt="Screen Shot 2021-08-23 at 3.20.08 PM" style="zoom:50%;" />

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.20.28 PM.png" alt="Screen Shot 2021-08-23 at 3.20.28 PM" style="zoom:50%;" />

# Solution:

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.22.26 PM.png" alt="Screen Shot 2021-08-23 at 3.22.26 PM" style="zoom:50%;" />

<img src="XSS & CSRF.assets/Screen Shot 2021-08-23 at 3.23.41 PM.png" alt="Screen Shot 2021-08-23 at 3.23.41 PM" style="zoom:50%;" />

# Resource:

It's time to try your hand at doing some bad things... but luckily in a safe playground. Try the below two exercises to get a better idea of how XSS and CSRF are used by malicious hackers:

1. [XSS](https://www.hacksplaining.com/exercises/xss-stored)

2. [CSRF](https://www.hacksplaining.com/exercises/csrf)

More resources:

[Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)

[Cookies with HTTPOnly and Secure headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)