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

