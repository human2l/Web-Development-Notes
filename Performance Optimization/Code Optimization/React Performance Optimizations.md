## React Performance Tool

**Note: add "/?react_perf" to the url to enable react performance tool. For example : "localhost:3000/?react_perf"**

Then in the performance tab, after recording, it will show how react working in detail.

<img src="React Performance Optimizations.assets/Screen Shot 2021-06-30 at 6.06.50 PM.png" alt="Screen Shot 2021-06-30 at 6.06.50 PM" style="zoom:50%;" />

## Redux question need to think:

 Do we need to connect redux to the top level components so that every time changes it will rerender many of their child components. Or connect to the leaf components to make it rerender less components? Both have pros and cons.

## Google Extension: React Developer Tools

<img src="React Performance Optimizations.assets/Screen Shot 2021-06-30 at 6.16.50 PM.png" alt="Screen Shot 2021-06-30 at 6.16.50 PM" style="zoom:50%;" />

Click on "Highlight Updates" and type or click a button to see what changes. Base on that, check and think if there are irrelevant elements rerendered when we interact with other elements.

## Question:

For example, when we type in the searchField, the header of the page rerendered, it is unnecessary.

## Solution:

1. Seperate the shouldn't-change element into a new element and use `shouldComponentUpdate()` or `React.memo()` to decide when it should rerendered. (DO NOT confuse `React.memo()` with `React.useMemo()`)

   Don't use `shouldComponentUpdate()` on every component because it will check if it need to be update every time. Might waste unnecessary time.

2. Change component to PureComponent. 

   PureComponent is a component that only changes when it's props changes.

**Warning: setState is asynchronous**: 

https://medium.com/@wereHamster/beware-react-setstate-is-asynchronous-ce87ef1a9cf3

https://vasanthk.gitbooks.io/react-bits/patterns/19.async-nature-of-setState.html

## Tools for checking unnecessary updates:

~~[Why did you update](https://github.com/maicki/why-did-you-update) enable warning on console when you do unnecessary updates.~~ Deprecated, use [Why Did You Render](https://www.npmjs.com/package/@welldone-software/why-did-you-render) instead.

