# Environmental Variables

```js
console.log(process.env.NODE_ENV)
```

will print: development (or) production

```js
if (process.env.NODE_ENV === 'production'){
	
}
```

### .env file

create-react-app will create .env file

```js
REACT_APP_SAY_HI = "HII"
```

then in react component

```js
console.log(process.env.REACT_APP_SAY_HI)
```

will print: HII in console

We shouldn't save the API key in github that everyone can see. Instead, we set it as environmental variable that can only be accessed from our local workplace.

<img src="Code Secrets.assets/Screen Shot 2021-08-23 at 9.53.02 PM.png" alt="Screen Shot 2021-08-23 at 9.53.02 PM" style="zoom:50%;" />

<img src="Code Secrets.assets/Screen Shot 2021-08-23 at 9.57.21 PM.png" alt="Screen Shot 2021-08-23 at 9.57.21 PM" style="zoom:50%;" />

```shell
npm install dotenv --save
```

Create-react-app uses above internally, if we are not in a react app, we can npm install it by ourselves.

# Commit History

We never want to put our secret files to github, use **.gitignore**

**DO NOT commit any secret to github!**

