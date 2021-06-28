# Parcel

Parcel is **zero** configuration. It will automatically generate dist folder and files in it.

```shell
mkdir parcel
cd parcel
npm install react react-dom
npm init -y
npm install --save-dev parcel-bundler babel-preset-env babel-preset-react
touch .babelrc
touch index.thml
touch index.js
```

### .babelrc

```json
{
	"presets": ["env", "react"]
}
```

### package.json

```json
{
	"scripts": {
		"start": "parcel index.html"
	}
}
```

### index.html

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Parcel</title>
  </head>
  <body>
    <div id="app"></div>
    <script src="./index.js"></script>
  </body>
</html>
```

### index.js

```react
import React from 'react';
import ReactDOM from 'react-dom';

const Hello = () => <div>WHATSUP?!</div>

ReactDOM.render(<Hello />, document.getElementById('app'))
```

