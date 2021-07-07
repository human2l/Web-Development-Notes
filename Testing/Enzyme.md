Enzyme is a useful tool to test **React** code
```shell
npm i --save-dev enzyme enzyme-adapter-react-16
```

### setupTests.js

```js
import { configure } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16'

configure({ adapter: new Adapter() });
```

### Card.test.js

```react
import { shallow, mount, render } from 'enzyme';
import React from 'react';
import Card from './Card';

it('expect to render Card component', () => {
	expect(shallow(<Card />).length).toEqual(1);  
})
```

**Note: **

**Shallow()** will only render the given component, will not render the child component inside the given component. 90% of cases we use shallow() instead of mount() and render()

**Mount()** does a full render of DOM, that means tests can affect each other if they're all using the same DOM

**Render()** does not render the whole DOM, it only render it as simple HTML

## Resources

To learn more about the 3 techniques used in Enzyme for testing: shallow, mount, render, have a look at [their api documentation](http://airbnb.io/enzyme/docs/api/) to see what kind of methods you can use to test your components.
