# initialise Next.js(legacy)
```shell
mkdir next-ssr
cd next-ssr/
npm init -y
npm install next react react-dom
```

### package.json

```json
"scripts": {
	"start": "next"
}
```

create a new folder: "pages"

```shell
npm start
```

# initialise Next.js

```shell
npm create-next-app
```

in folder pages:

### index.js

```react
//no need to import react, all handled by Next.js
//To use client side routing, we use "Link"
import Link from 'next/link';

const Index = () => (
	<div>
  	<h1>SSR Magician</h1>
    {/*Server side routing:*/}
    {/*<a href='./about'>About</a>*/}
    {/*Client side routing:*/}
    <Link href='/about'>
    	<a>About</a>
      {/*or*/}
      <button>About</button>
    </Link>
    
  </div>
)

export default Index
```

above will shown in localhost:3000

### about.js

```react
import Link from 'next/link';
const About = () => (
	<div style={{fontSize: '20px', color: 'blue'}}>
  	<h1>About</h1>
    <Link href='/'>
    	<button>Back</button>
    </Link>
    <p>I was a magician once</p>
  </div>
)

export default About;
```

above will be shown in localhost:3000/about

## Server side routing vs Client side routing

https://medium.com/@wilbo/server-side-vs-client-side-routing-71d710e9227f

# Shared components

Create a folder: components. In components folder:

### image.js

```react
cosnt Image = () =>(
	<img src='blahblah'/>
)

export default Image;
```

### about.js

```react
import Link from 'next/link';
import Image from '../components/Image'

const About = () => (
	<div style={{fontSize: '20px', color: 'blue'}}>
  	<h1>About</h1>
    <Link href='/'>
    	<button>Back</button>
    </Link>
    <Image />
    <p>I was a magician once</p>
  </div>
)

export default About;
```

# Dynamic Apps with Next.js

```shell
npm install isomorphic-unfetch
```

in pages folder:

### robots.js

```react
import Link from 'next/link';
import fetch from 'isomorphic-unfetch';

const Robots = (props) => {
	return (
		<div>
    	<h1>Robots</h1>
      <Link href='/'>
      	<button>Home</button>
      </Link>
      <div>
      	{
          props.robots.map(robot => (
          	<li key={robot.id}>
              <Link href={`robots/${robot.id}`}>
                <a>{robot.name}</a>
              </Link>
            </li>
          ))
        }
      </div>
    </div>		
	)
}

Robots.getInitialProps = async function() {
  const res = await fetch('https://jsonplaceholder.typicode.com/users')
  const data = await res.json();
  //Initial refresh the page: console.log will show on server
  //Revisiting the page: console.log will show on client
  console.log(data)
  return {
    robots: data
  }
}

export default Robots;
```

### Index.js

```react
import Link from 'next/link';

const Index = () => (
	<div>
  	<h1>SSR Magician</h1>
    <Link href='/about'>
      <button>About</button>
    </Link>
    <Link href='/robots'>
    	<button>Robots</button>
    </Link>
  </div>
)

export default Index
```

**Note:**

\1. It's recommended to use `getStaticProps` or `getServerSideProps` for data fetching now instead of `getInitialProps`:
https://nextjs.org/docs/api-reference/data-fetching/getInitialProps

\2. We no longer need to import isomorphic-unfetch. So update the code by removing it:
https://nextjs.org/blog/next-9-4#improved-built-in-fetch-support

# Deploy Next.js App

https://zeit.co/now

# Update next.js

```shell
npm i next@latest react@latest react-dom@latest
```



