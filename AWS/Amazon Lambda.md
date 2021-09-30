function will be store in Amazon database, whenever a function need to be called, Amazon find this function in database and put it into containers, and provide each user a container.

Because it is stored in database, when it first runs a function, it takes a little bit of time. (like we build docker container)

Amazon only charge when it runs

# Serverless

Serverless will take care of all the aws configuration for us

```bash
npm install serverless
```

```bash
serverless create --help
```

Note: we can use "sls" as a short hand of "serverless"

<img src="Amazon Lambda.assets/Screen Shot 2021-09-29 at 6.29.41 PM.png" alt="Screen Shot 2021-09-29 at 6.29.41 PM" style="zoom:50%;" />

```bash
sls create -t aws-nodejs
```

-t: template

Three file will be generated:

<img src="Amazon Lambda.assets/Screen Shot 2021-09-29 at 6.37.17 PM.png" alt="Screen Shot 2021-09-29 at 6.37.17 PM" style="zoom:50%;" />

## IAM(Identity and Access Management)

1. Go to aws search IAM service
2. Add new user
3. Give user permission(AdministratorAccess for now)

<img src="Amazon Lambda.assets/Screen Shot 2021-09-29 at 9.31.00 PM.png" alt="Screen Shot 2021-09-29 at 9.31.00 PM" style="zoom:50%;" />

```bash
sls config credentials --provider aws --key [Access key ID] --secret [Secret access key]
```

The command above create a folder under root folder:  `~/.aws` and create a file `credentials` contains the access key ID and secret

```bash
cd ~/.aws
nano credentials
```

<img src="Amazon Lambda.assets/Screen Shot 2021-09-29 at 9.39.05 PM.png" alt="Screen Shot 2021-09-29 at 9.39.05 PM" style="zoom:50%;" />

## serverless.yml

```yaml
#blahblah
service: awsTest
provider:
  name: aws
  runtime: nodejs12.x
  lambdaHashingVersion: 20201221

  # you can overwrite defaults here
  #  stage: prod
  stage: dev
  
functions:
  test:
    handler: handler.test
#blahblah
```



## handler.js

stateless function, not store any data

```js
"use strict";

module.exports.test = async (event) => {
  return {
    statusCode: 200,
    body: JSON.stringify(
      {
        message: "Go Serverless v1.0! Your function executed successfully!",
        input: event,
      },
      null,
      2
    ),
  };
```



```bash
sls deploy
```

<img src="Amazon Lambda.assets/Screen Shot 2021-09-30 at 6.34.56 PM.png" alt="Screen Shot 2021-09-30 at 6.34.56 PM" style="zoom:50%;" />


```bash
sls invoke --function [function name]
```

<img src="Amazon Lambda.assets/Screen Shot 2021-09-30 at 6.35.25 PM.png" alt="Screen Shot 2021-09-30 at 6.35.25 PM" style="zoom:50%;" />

We can add a "local" `sls invoke local --function [function name]` which try and simulate the lambda function and run locally so that we won't get charged. 

## serverless.yml

```yaml
#blahblah
functions:
  test:
    handler: handler.test
    events:
      - httpApi:
          path: /users/create
          method: get
#blahblah
```

After `sls deploy`, we have an endpoint:

![Screen Shot 2021-09-30 at 6.47.36 PM](Amazon Lambda.assets/Screen Shot 2021-09-30 at 6.47.36 PM.png)

which can be access by http request:

<img src="Amazon Lambda.assets/Screen Shot 2021-09-30 at 6.48.35 PM.png" alt="Screen Shot 2021-09-30 at 6.48.35 PM" style="zoom:50%;" />

# use parameters

## handler.js

<img src="Amazon Lambda.assets/Screen Shot 2021-09-30 at 7.50.59 PM.png" alt="Screen Shot 2021-09-30 at 7.50.59 PM" style="zoom:50%;" />

<img src="../../../Library/Application Support/typora-user-images/Screen Shot 2021-09-30 at 7.51.34 PM.png" alt="Screen Shot 2021-09-30 at 7.51.34 PM" style="zoom:50%;" />

# Resources:

## IAM

To learn more about IAM policies, you can check out [the official documentation from Amazon](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html), or [this documentation](https://serverless.com/framework/docs/providers/aws/guide/iam/) from the Serverless framework

