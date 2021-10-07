# CircleCI pipeline

circleci.com

in project folder, create folder: `.circleci` inside .circleci create: `config.yml`

## config.yml

```yaml
version: 2.1
jobs:
   build:
     docker:
       - image: circleci/node:latest
     steps:
       - checkout
       - run: npm install
       - run: CI=true npm run build
   test:
     docker:
       - image: circleci/node:latest
     steps:
       - checkout
       - run: npm install
       - run: npm run test
   hithere:
     docker:
       - image: circleci/node:latest
     steps:
       - checkout
       - run: echo "Hellloooo!"
workflows:
  version: 2
  build-test-and-lint:
    jobs:
      - build
      - hithere
      - test:
          requires:
            - hithere
```

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.02.59 PM.png" alt="Screen Shot 2021-10-07 at 10.02.59 PM" style="zoom:50%;" />

```bash
git status
git checkout -b testing
git add .
git push orgin testing
```

There will be a pull request:

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.04.17 PM.png" alt="Screen Shot 2021-10-07 at 10.04.17 PM" style="zoom:50%;" />

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.04.45 PM.png" alt="Screen Shot 2021-10-07 at 10.04.45 PM" style="zoom:50%;" />

Click "Create pull request"

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.05.18 PM.png" alt="Screen Shot 2021-10-07 at 10.05.18 PM" style="zoom:50%;" />

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.05.40 PM.png" alt="Screen Shot 2021-10-07 at 10.05.40 PM" style="zoom:50%;" />

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.05.58 PM.png" alt="Screen Shot 2021-10-07 at 10.05.58 PM" style="zoom:50%;" />

click "Workflow":

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.06.23 PM.png" alt="Screen Shot 2021-10-07 at 10.06.23 PM" style="zoom:50%;" />

After a while:

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.07.38 PM.png" alt="Screen Shot 2021-10-07 at 10.07.38 PM" style="zoom:50%;" />

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.07.54 PM.png" alt="Screen Shot 2021-10-07 at 10.07.54 PM" style="zoom:50%;" />

Now wait for a Code Review by a team member now(instead of click"Merge pull request")

## Add prettier

### Install

prettier.io/docs/en/install.html:

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.19.23 PM.png" alt="Screen Shot 2021-10-07 at 10.19.23 PM" style="zoom:50%;" />

### Pre-commit Hook

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.18.29 PM.png" alt="Screen Shot 2021-10-07 at 10.18.29 PM" style="zoom:50%;" />

```bash
git status
git checkout -b prettier
git add .
git commit =m"pretty please"
```

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.21.16 PM.png" alt="Screen Shot 2021-10-07 at 10.21.16 PM" style="zoom:50%;" />

Now prettier runs everytime before commit, and it ONLY runs on files that we changes(won't modify other files, good!)

```bash
git push origin prettier
```

## webpack-bundle-analyzer

use to generate an image that store on server, will show the amount of files in build

<img src="CircleCI.assets/Screen Shot 2021-10-07 at 10.24.54 PM.png" alt="Screen Shot 2021-10-07 at 10.24.54 PM" style="zoom:50%;" />

If you want to limit your JavaScript files to one hundred megabytes, you can run those tests. And any time a new feature is added that might push you over one hundred megabytes, you can make the test fail.
