# server code

```shell
npm install jsonwebtoken
```



```js
const jwt = require('jsonwebtoken')

const signToken = (email) => {
  //payload is something useful later(should not be sensitive data)
  const jwtPayload = { email };
	//'JWT_SECRET' should be a secret key only know by developer. should put it in configuration file, i.e. process.env.JWT_SECRET
  //For now we just use the string
  return jwt.sign(jwtPayload, 'JWT_SECRET', {expiresIn: '2 days'})
  
}

//Params: user -- After user registered/logged in, an other function will return this user object that contains user's info
const createSessions = (user) => {
  // JWT token, return user data
  const { email, id } = user;
  const token = signToken(email);
  //Only send id to the front end, front end will GET: profile/:id to get the full info of user
  return { success: 'true', userId: id, token: token}
}
```

