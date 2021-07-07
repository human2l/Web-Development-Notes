## Problem:

if we try write app.test.js like this:

### App.test.js

```react
import { shallow } from 'enzyme';
import React from 'react';
import App from './App';

it('expect to render App component', () => {
  const mockStore = {
    robots: [],
    searchField: ''
  }
	expect(shallow(<App store={mockStore} />)).toMatchSnapshot();
}
```

#### Optional: 

There is a tool called `redux-mock-store` can help us update the redux store test file when our project updating.

Because App is wrapped by connect(), a common option is to expport the App Component: `export class App extents Component` and import just the App Component into our tests. But we are going to do something even better.

## Solution: 

We divided the old App.js to two seperate components: App.js and MainPage.js

### containers/App.js

```react
import React, { Component } from 'react';
import { connect } from 'react-redux';
import { setSearchField, requestRobots } from '../actions';

import MainPage from '../components/MainPage'

import './App.css';

const mapStateToProps = (state) => {
  return {
    searchField: state.searchRobots.searchField,
    robots: state.requestRobots.robots,
    isPending: state.requestRobots.isPending
  }
}

const mapDispatchToProps = (dispatch) => {
  return {
    onSearchChange: (event) => dispatch(setSearchField(event.target.value)),
    onRequestRobots: () => dispatch(requestRobots())
  }
}

class App extends Component {
  render() {
    return <MainPage {...this.props}/>
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(App)
```

### components/MainPage.js

```react
import React, { Component } from 'react';

import CardList from './CardList';
import SearchBox from './SearchBox';
import Scroll from './Scroll';
import ErrorBoundry from './ErrorBoundry';
import Header from './Header';

export class MainPage extends Component {
  componentDidMount() {
    this.props.onRequestRobots();
  }

  filterRobots = () => {
    const { robots, searchField } = this.props;
    return robots.filter(robot => {
      return robot.name.toLowerCase().includes(searchField.toLowerCase());
    })
  }

  render() {
    const { onSearchChange, isPending } = this.props;

    return (
      <div className='tc'>
        <Header />
        <SearchBox searchChange={onSearchChange}/>
        <Scroll>
          { isPending ? <h1>Loading</h1> :
            <ErrorBoundry>
              <CardList robots={this.filterRobots()} />
            </ErrorBoundry>
          }
        </Scroll>
      </div>
    );
  }
}

export default MainPage
```

### components/MainPage.test.js

```react
import React from 'react';
import { Provider } from 'react-redux';
import { shallow } from 'enzyme';
import MainPage from './MainPage';

let wrapper;

//beforeEach() makes sure that it runs before each of the tests
beforeEach(() => {
  const mockProps = {
    onRequestRobots: jest.fn(),
    robots: [],
    searchField: '',
    isPending: false
  }
  wrapper = shallow(<MainPage {...mockProps}/>)
 })

it('renders without crashing', () => {
  expect(wrapper).toMatchSnapshot();
});

it('fileters Robots', () => {
  const mockProps = {
    onRequestRobots: jest.fn(),
    robots: [],
    searchField: 'a',
    isPending: false
  }
  wrapper = shallow(<MainPage {...mockProps}/>)
  expect(wrapper.instance().filterRobots()).toEqual([]);
});

it('fileters Robots correctly', () => {
  const filteredRobots = [{
    id: 1,
    name: 'Leanne Graham',
    username: 'Bret',
    email: 'Sincere@april.biz'
  }]
  const mockProps = {
    onRequestRobots: jest.fn(),
    robots: [{
      id: 1,
      name: 'Leanne Graham',
      username: 'Bret',
      email: 'Sincere@april.biz'
    }],
    searchField: 'Leanne',
    isPending: false
  }
  wrapper = shallow(<MainPage {...mockProps}/>)
  expect(wrapper.instance().filterRobots()).toEqual(filteredRobots);
});

it('fileters Robots correctly 2', () => {
  const filteredRobots = [{
    id: 1,
    name: 'Leanne Graham',
    username: 'Bret',
    email: 'Sincere@april.biz'
  }]
  const mockProps = {
    onRequestRobots: jest.fn(),
    robots: [{
      id: 1,
      name: 'Leanne Graham',
      username: 'Bret',
      email: 'Sincere@april.biz'
    }],
    searchField: 'Xavier',
    isPending: false
  }
  wrapper = shallow(<MainPage {...mockProps}/>)
  expect(wrapper.instance().filterRobots()).toEqual([]);
});
```

