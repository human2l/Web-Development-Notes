TypeScript is a super set of javascript

## install

```shell
sudo npm install -g typescript
tsc
```

tsc is command to show detailed information of typescript

```shell
mkdir type
cd type
touch typescript.ts
```

### typescript.ts

```typescript
const sum = (a,b) => {
	return a + b;
}
```
```shell
tsc typescript.ts
```

it will create a `typescript.js` file:

### typescript.js

```js
var sum = function (a, b) {
	return a + b;
}
```

------

### typescript.ts

```ts
const sum = (a : number, b : number) => {
	return a + b;
}
const answer = sum (4, 5);
console.log(answer);
const answer = sum ('hello', 5); //editor will show error before run
//it still generate the runnable javascript file, but typescript will show error before it runs.
console.log(answer);
```

**Note: typescript catch the error when we convert .ts to .js**

## Create config file

```shell
tsc --init
```

will create tsconfig.json

## Using watch mode

```shell
tsc typescript.ts --watch
```

## Type

```ts
// boolean
let isCool: boolean = true;

// number
let age: number = 56;

// string
let eyeColor: string = 'brown';
let favouriteQuote: string = `I'm not old, i'm only ${age}`;

// Array
let pets: string[] = ['cat', 'dog', 'pig']
let pets2: Array<string> = ['lion', 'dragon', 'lizard']

// Object
let wizard: object = {
  a: 'John'
}

// null and undefined
let meh: undefined = undefined;
let noo: null = null;

// Tuple
let basket: [string, number];
basket = ['basketball', 5]

// Enum
enum Size { Small = 1, Medium = 2, Large = 3}
let sizeName: string = Size[2]; //Medium
let sizeName2: number = Size.Small; //1

// Any - !!!!!!!! BE CAREFUL
let whatever: any = 'noooooooooo!!!!';
whatever = 5; //no error
whatever = true; //no error
whatever = Size.small; //no error
whatever = basket; //no error

// void
let sing = (): void => {
  console.log('lalalala')
  return 'lala' //error should return nothing
}

// never
let error = (): never => {
  throw Error('ooops')// no error, because it shouldn't return and shouldn't have an endpoint
}

// interface
interface RobotArmy {
  count: number,
  type: string,
  magic: string,
}
let fightRobotArmy = (robots: RobotArmy) => {
  console.log('FIGHT!')
}// equal to below
let fightRobotArmy2 = (robots: {count: number, type: string, magic: string}) => {
  console.log('FIGHT!')
}
type RobotArmy = {
  count: number,
  type: string,
  magic: string,
}// using type will do the same

// Type Assertion
interface CatArmy {
  count: number,
  type: string,
  magic: string,
}
let dog = {} as CatArmy
dog.count // no error because we did a type assertion

// Optional Property
interface RobotArmy {
  count: number,
  type: string,
  magic?: string,
}
fightRobotArmy({count: 1, type: 'dragon'})// not error, because we make magic an optional property

// Function
let fightRobotArmy3 = (robots: RobotArmy): void => {
  console.log('FIGHT!')
}
let fightRobotArmy4 = (robots: {count: number, type: string, magic: string}): number => {
  console.log('FIGHT!')
  return 5
}

// Classes
class Animal {
  private sing: string = 'alalala'// By default is public, now we set it to private
  constructor(sound: string) {
    this.sing = sound;
  }
  greet(): string {
    return `Hello ${this.sing}`
  }
}

let lion = new Animal('RAAWWWR')
lion.greet()
lion.sing // error occurs, because we set sing to private

// Union
let confused: string | number = "hello"
let confused: string | number = 5

let x: number = 4
x = 'hello'
```



# Resources

## Type vs Interface

To learn more about the difference between `type` and `interface` :

https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c

https://stackoverflow.com/questions/37233735/typescript-interfaces-vs-types

## Type Assertion

Type Assertion is another complex topic. If you want to learn more about it, I recommend you read this:

https://basarat.gitbook.io/typescript/type-system/type-assertion
