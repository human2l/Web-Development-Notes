# Adding TypeScript

### 1. Uninstall the create-react-app package

```shell
npm uninstall -g create-react-app
```

### 2. add typescript

```shell
npx create-react-app my-app --typescript
npm install --save typescript @types/node @types/react @types/react-dom @types/jest
```

### 3. rename any file to be a TypeScript file (e.g. src/index.js to src/index.tsx)

**Note: Only convert the files where we will use TypeScript**

A `tsconfig.json` will be created

## Examples

```ts
interface CardStatelessProps {
  name: string,
  email: string,
  id: number
}
//SFC means stateless functional component
const Card: React.SFC<CardStatelessProps> = ({ name, email, id }) => {
}
```

```jsx
type Props {
	children?: JSX.Element
}
const Scroll = (props: Props) => {
	return (
		<div>
			{props.children}
		</div>
	)
}
```

```react
//What onSearchChange function looks like:
/*
onSearchChange = (event) => {
	this.setState({BLAHBLAHBLAH....})
}
*/

interface ISearchBoxProps {
	searchChange(event: React.SyntheticEvent<HTMLInputElement>): void
}

const SearchBox = ({ searchChange }: ISearchBoxProps) = > {
  return (
  	<div>
  		<input
      	onChange={searchChange}  
      />
  	</div>
  )
}
```



```react
interface IAppProps {
}

interface IAppState {
	robots: Array<IRobot>;
	searchfield: string;
}
class App extends React.Component<IAppProps, IAppState> {
  constructor(props: IAppProps){
    super(props)
    this.state = {
      robots: [],
      searchfield: ''
    }
  
  onSearchChange = (event: React.SyntheticEvent<HTMLInputElement>): void => {
		this.setState({BLAHBLAHBLAH....})
	}
    
  }
	//BLAHBLAH
  
  render(): JSX.Element {
    //BLAHBLAH
  }
}
```

## Resources

https://github.com/aneagoie/robofriends-typescript-completed