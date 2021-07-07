### Three main categories:

<img src="Index.assets/Screen Shot 2021-07-01 at 5.35.02 PM.png" alt="Screen Shot 2021-07-01 at 5.35.02 PM" style="zoom:50%;" />

### Resources

You can find all the code used in this section with the latest up to date libraries below if you encounter any issues:

[**https://github.com/aneagoie/testing-exercise**](https://github.com/aneagoie/testing-exercise)

[**https://github.com/aneagoie/robofriends-testing**](https://github.com/aneagoie/robofriends-testing)

### Testing Libraries

Scaffolding | Assertion library | Test Runner | Spies, Mocks and Stubs | Code Coverage

<img src="Index.assets/Screen Shot 2021-07-01 at 6.31.56 PM.png" alt="Screen Shot 2021-07-01 at 6.31.56 PM" style="zoom:50%;" />

Create-react-app uses Jest (Created by Facebook)

<img src="Index.assets/Screen Shot 2021-07-01 at 6.37.03 PM.png" alt="Screen Shot 2021-07-01 at 6.37.03 PM" style="zoom:50%;" />

## Unit Tests

Cover all small pure functions. Main principle of functional programming. It don't test the contract (a connection between things, like contract between a server and a database, or a function to another function)

## Integration Tests

All about cross communication between differents units of code. For example, mock database call. They are expensive and slower. They can be really fragile and much harder to write. It's impossible to cover all of the things, so It's hard to say when you have this one hundred percent completion. Rare to see in a company has really good integration tests unless they're massive company and ton of money spent.

## Automation Tests

These are the hardest to set up. Because users have tons of different environments they run the app. Cost a lot more money and time.

Companies providing automation tests:

<img src="Index.assets/Screen Shot 2021-07-01 at 6.49.01 PM.png" alt="Screen Shot 2021-07-01 at 6.49.01 PM" style="zoom:50%;" />

Because we want to test the entire process of UI, many companies hire people to do automation tests.

------

<img src="Index.assets/Screen Shot 2021-07-01 at 6.53.48 PM.png" alt="Screen Shot 2021-07-01 at 6.53.48 PM" style="zoom:50%;" />

1. Jest_Testing
2. Enzyme
3. Snapshot Testing
4. Testing Connected Components
5. Testing Reducers
6. Testing Actions

