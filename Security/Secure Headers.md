```shell
npm install helmet
```

Before using helmet:

![Screen Shot 2021-08-23 at 10.51.20 PM](Secure Headers.assets/Screen Shot 2021-08-23 at 10.51.20 PM.png)

We can see headers like X-Powered-By: Express. Then people would know that our server is built with express

After we using helmet

<img src="Secure Headers.assets/Screen Shot 2021-08-23 at 10.52.29 PM.png" alt="Screen Shot 2021-08-23 at 10.52.29 PM" style="zoom:50%;" />

Helmet will create all the securtity headers for us:

<img src="Secure Headers.assets/Screen Shot 2021-08-23 at 10.53.56 PM.png" alt="Screen Shot 2021-08-23 at 10.53.56 PM" style="zoom:50%;" />

<img src="Secure Headers.assets/Screen Shot 2021-08-23 at 10.55.14 PM.png" alt="Screen Shot 2021-08-23 at 10.55.14 PM" style="zoom:50%;" />

Now we have all the guards for us.

And we don't need to add headers like below by ourselves:

<img src="Secure Headers.assets/Screen Shot 2021-08-23 at 10.56.10 PM.png" alt="Screen Shot 2021-08-23 at 10.56.10 PM" style="zoom:50%;" />

# Resources:

1. If you are new to HTTP: https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177
2. To learn a little bit more about HTTP Headers: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
3. HTTP Header Fields: https://www.tutorialspoint.com/http/http_header_fields.htm
4. Helmet package documentation: https://github.com/helmetjs/helmet

