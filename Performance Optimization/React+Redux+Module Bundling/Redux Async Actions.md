When calling an api or other side effect actions, we should do it asynchronous way by using middleware. 

We can use Redux Thunk to handle asynchronous actions like Ajax calls

# Redux Thunk

`$npm install redux-thunk`

# index.js

```react
import { createStore, applyMiddleware, combineReducers } from 'redux';
import { searchRobots, requestRobots } from './reducers'
import thunkMiddleware from 'redux-thunk'

const logger = createLogger();
const rootReducer = combineReducers({ searchRobots, requestRobots })
const store = createStore(rootReducer, applyMiddleware(thunkMiddleware,logger))
```

**Note: Remember to change "searchField: state.searchField" to "searchField: state.searchRobots.searchField" in mapStateToProps of App.js**

# constants.js

```react
export const REQUEST_ROBOTS_PENDING = 'REQUEST_ROBOTS_PENDING'
export const REQUEST_ROBOTS_SUCCESS = 'REQUEST_ROBOTS_SUCCESS'
export const REQUEST_ROBOTS_FAILED = 'REQUEST_ROBOTS_FAILED'
```

# actions.js

```react
import {REQUEST_ROBOTS_PENDING,REQUEST_ROBOTS_SUCCESS,REQUEST_ROBOTS_FAILED} from './constants.js'

//Example function. It returns an object
export const setSearchField = (text) => ({
	type: CHANGE_SEARCH_FIELD,
	payload: text
})

//Returns a function, then Thunk will handle this
//first way:
export const requestRobots = (dispatch) => {
//or second way:
export const requestRobots = () => (dispatch) => {
  dispatch({ type: REQUEST_ROBOTS_PENDING });
  fetch('https://jsonplaceholder.typicode.com/users')
  	.then(response => response.json())
	  .then(data => dispatch({ type: REQUEST_ROBOTS_SUCCESS, payload: data}))
  	.catch(error => dispatch({ type: REQUEST_ROBOTS_FIELD, payload: error}))
}
```

**Note: change app.js to the same first/second way**

requestRobots returns a function instead of an object. Redux doesn't recognize it. However, when installed Thunk.

Thunk will check actions.js to find if any functions return a function instead of an object. Then apply on these functions.

# reducers.js

```react
import {REQUEST_ROBOTS_PENDING,REQUEST_ROBOTS_SUCCESS,REQUEST_ROBOTS_FAILED} from './constants.js'

const initialStateRobots = {
  isPending: false,
  robots: [],
  error: ''
}

export const requestRobots = (state=initialStateRobots, action={})=> {
  switch(action.type) {
    case REQUEST_ROBOTS_PENDING:
      return {...state, isPending : true}
    case REQUEST_ROBOTS_SUCCESS:
      return {...state, robots: action.payload, isPending: false }
    case REQUEST_ROBOTS_FAILED:
      return {...state, error: action.payload, isPending: false }
    default:
      return state;
  }
}
```

# app.js

```react
componentDidMount() {
  this.props.onRequestRobots()
}

const mapDispatchToProps = (dispatch) => {
	return {
    //onSearchChange: (event) => dispatch(setSearchField(event.target.value))
    //first way:
    onRequestRobots: () => requestRobots(dispatch);
    //Second way:
    onRequestRobots: () => dispatch(requestRobots());
  }
}

render(){
  const { searchField, onSearchChange, robots, isPending } = this.props
  
}
```

**Note: change actions.js to the same first/second way**