For debugging purpose

`$npm install redux-logger`

# Index.js

```react
import { applyMiddleware } from 'redux'
import { createLogger } from 'redux-logger'

const logger = createLogger;
//was: const sotre = createStore(searchRobots)
//change to: 
const store = createStore(searchRobots, applyMiddleware(logger));
```

![Screen Shot 2021-06-27 at 5.35.58 PM](Redux Logger Middleware.assets/Screen Shot 2021-06-27 at 5.35.58 PM.png)

Now when typing in search field, console will show redux state.

# Additional:

### Redux DevTools

A more powerful way to monitoring Redux during coding process.

