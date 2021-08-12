# React Server Side Rendering

![Screen Shot 2021-08-12 at 7.33.37 PM](Server Side Rendering React.assets/Screen Shot 2021-08-12 at 7.33.37 PM.png)

On server side, `renderToString()` convert react app into a string and send through the wire to client side. On client side, `hydrate()` attach event listeners so that user can interact with the page.

`renderToNodeStream()` is a new function similar to `renderToString()` on ReactDOMServer that makes the process more faster.

![Screen Shot 2021-08-12 at 7.40.27 PM](Server Side Rendering React.assets/Screen Shot 2021-08-12 at 7.40.27 PM.png)