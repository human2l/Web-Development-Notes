```shell
npm install morgan
npm install winston
```

## Morgan

```shell
npm install morgan
```

```js
const morgan = require('morgan')
const app = express()
app.use(morgan('tiny'))
```

<img src="Logging.assets/Screen Shot 2021-08-22 at 10.43.55 PM.png" alt="Screen Shot 2021-08-22 at 10.43.55 PM" style="zoom:50%;" />

```js
app.use(morgan('combined'))
```

<img src="Logging.assets/Screen Shot 2021-08-22 at 10.44.13 PM.png" alt="Screen Shot 2021-08-22 at 10.44.13 PM" style="zoom:50%;" />

## Winston

```shell
npm install winston
```

```js
const winston = require('winston')

app.post('/secret', (req,res) => {
	const {userInput} = req.body;
	//console.log(userInput);
	winston.log('info',userInput);
})
```

<img src="Logging.assets/Screen Shot 2021-08-22 at 10.47.42 PM.png" alt="Screen Shot 2021-08-22 at 10.47.42 PM" style="zoom:50%;" />

Bad example:

<img src="Logging.assets/Screen Shot 2021-08-22 at 10.53.10 PM.png" alt="Screen Shot 2021-08-22 at 10.53.10 PM" style="zoom:50%;" />

Note: DO NOT show user the infomation that "user already exists" because hacker will use this info to attack. Instead, use logging to only let people from backend see what happened.