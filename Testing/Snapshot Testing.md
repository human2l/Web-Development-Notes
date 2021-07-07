### Card.test.js

```react
import { shallow, mount, render } from 'enzyme';
import React from 'react';
import Card from './Card';

it('expect to render Card component', () => {
	expect(shallow(<Card />)).toMatchSnapshot();
}
```

Jest will create a folder called `__snapshots__` it takes a picture of the component. If we change anything in the component, for example the className, it will fail the test and show the difference. Make sure the `__snapshots__` go with source control (e.g. github)

<img src="Snapshot Testing.assets/Screen Shot 2021-07-07 at 2.22.49 PM.png" alt="Screen Shot 2021-07-07 at 2.22.49 PM" style="zoom:50%;" />

Press u to update the snapshot.

### Show test coverage

```shell
npm test -- --coverage
```

**Note: try write pure functions to make testing sample**

## Test component with props

### CardList.test.js

```react
import { shallow } from 'enzyme';
import React from 'react';
import Card from './CardList';

it('expect to render CardList component', () => {
  const mockRobots = [
    {
      id: 1,
      name: 'John Snow',
      username: 'JohnJohn',
      email: 'john@gmail.com'
    }
  ]
	expect(shallow(<CardList robots={mockRobots} />)).toMatchSnapshot();
}
```

## Test Stateful Components

### CounterButton.test.js

```react
import { shallow } from 'enzyme';
import React from 'react';
import CounterButton from './CounterButton';

it('expect to render CounterButton component', () => {
  const mockColor = 'red'
	expect(shallow(<CounterButton color={mockColor} />)).toMatchSnapshot();
}

it('correctly increments the counter', () => {
  const mockColor = 'red'
  count wrapper = shallow(<CounterButton color={mockColor} />)
  
  //Remember to give an "id" property to counter button
  wrapper.find('[id=counter]').simulate('click')
  wrapper.find('[id=counter]').simulate('click')
  expect(wrapper.state()).toEqual({ count: 2 });
  wrapper.find('[id=counter]').simulate('click')
  expect(wrapper.state()).toEqual({ count: 3 });
  wrapper.find('[id=counter]').simulate('keypress')
  expect(wrapper.state()).toEqual({ count: 3 });//pass because keypress doesn't affect count
  expect(wrapper.props().color).toEqual('red')
})
```

