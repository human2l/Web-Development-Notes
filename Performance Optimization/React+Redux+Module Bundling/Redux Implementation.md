# actions.js

```react
import { CHANGE_SEARCH_FIELD } from './constants.js'

export const setSearchField = (text) => ({
	type: CHANGE_SEARCH_FIELD,
	payload: text
})
```

Payload is whatever send to the reducer

# constants.js

```react
export const CHANGE_SEARCH_FIELD = 'CHANGE_SEARCH_FIELD'
```

# reducers.js

```react
import { CHANGE_SEARCH_FIELD } from './constants.js'

const initialState = {
	searchField: ''
}
export const searchRobots = (state=initialState, action={}) => {
  switch(action.type) {
     case CHANGE_SEARCH_FIELD:
      //return Object.assign({}, state, {searchField: action.payload})
      //or
      return {...state, searchField: action.payload}
    default:
      return state;
  }
}
```

# index.js

```react
import { Provider } from 'react-redux';
import { createStore } from 'redux';
import { searchRobots } from './reducers';

// should be: const store = createStore(rootReducer);
// For now, we use
const sotre = createStore(searchRobots)

ReactDom.render(
  <Provider store={store} >
  	<App/>
  </Provider>
  , document.getElementById('root'));
```

# app.js

```react
import { connect } from 'react-redux';
import { setSearchField } from '../actions'

/*
normal codes here......
*/

const mapStateToProps = state => {
  return {
    searchField: state.searchRobots.searchField
  }
}

const mapDispatchToProps = (dispatch) => {
  return {
	  onSearchChange: (event) => dispatch(setSearchField(event.target.value))    
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(App)

```

