# Principal of least privilege

## CORS

```shell
npm install cors
```

```js
const express = require('express')
const cors = require('cors')
const app = express();
app.use(cors())
```

If we don't have CORS:

<img src="Access Control.assets/Screen Shot 2021-08-23 at 11.02.31 PM.png" alt="Screen Shot 2021-08-23 at 11.02.31 PM" style="zoom:50%;" />

For example, setup whitelist:

<img src="Access Control.assets/Screen Shot 2021-08-23 at 11.05.03 PM.png" alt="Screen Shot 2021-08-23 at 11.05.03 PM" style="zoom:50%;" />

Note: To temporary pass the CORS, we can add a header on http request to avoid errors. Don't do this on production:

<img src="Access Control.assets/Screen Shot 2021-09-30 at 8.07.25 PM.png" alt="Screen Shot 2021-09-30 at 8.07.25 PM" style="zoom:50%;" />

