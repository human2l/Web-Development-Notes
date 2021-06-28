# Redux

![Screen Shot 2021-06-27 at 3.58.04 PM](Redux.assets/Screen Shot 2021-06-27 at 3.58.04 PM.png)

<img src="Redux.assets/Screen Shot 2021-06-27 at 3.58.21 PM.png" alt="Screen Shot 2021-06-27 at 3.58.21 PM" style="zoom:33%;" />

![Screen Shot 2021-06-27 at 3.58.51 PM](Redux.assets/Screen Shot 2021-06-27 at 3.58.51 PM.png)

The concept is mimic the way we design database:  There are many users simutanously read or modify database, we need a way to avoid bugs and errors.

### Flux Pattern vs MVC Pattern: 

![Screen Shot 2021-06-27 at 3.59.22 PM](Redux.assets/Screen Shot 2021-06-27 at 3.59.22 PM.png)

![Screen Shot 2021-06-27 at 3.59.38 PM](Redux.assets/Screen Shot 2021-06-27 at 3.59.38 PM.png)

#### Without Redux:

(Blue dots trigger the state change and make the tree rerender)

![Screen Shot 2021-06-27 at 4.01.53 PM](Redux.assets/Screen Shot 2021-06-27 at 4.01.53 PM.png)

![Screen Shot 2021-06-27 at 4.02.04 PM](Redux.assets/Screen Shot 2021-06-27 at 4.02.04 PM.png)

#### With Redux:

<img src="Redux.assets/Screen Shot 2021-06-27 at 4.00.42 PM.png" alt="Screen Shot 2021-06-27 at 4.00.42 PM" style="zoom:40%;" />

# Install Redux

`$npm install redux`

`$npm install react-redux`

**Note: Try using "Redux Toolkit" to simplify the boilerplate redux code**

<img src="Redux.assets/Screen Shot 2021-06-27 at 5.14.39 PM.png" alt="Screen Shot 2021-06-27 at 5.14.39 PM" style="zoom:50%;" />

**Note: Yellow dots is components that implemented connect() function of Redux**

