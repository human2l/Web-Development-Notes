# bcrypt, scrypt, Aragon2

For example, our password is: "soup"

<img src="Data Management.assets/Screen Shot 2021-08-23 at 11.14.32 PM.png" alt="Screen Shot 2021-08-23 at 11.14.32 PM" style="zoom:50%;" />

We only save the hashed data into database.

<img src="Data Management.assets/Screen Shot 2021-08-23 at 11.16.08 PM.png" alt="Screen Shot 2021-08-23 at 11.16.08 PM" style="zoom:50%;" />

Each time we receive user's password, we use compare to check if the hashed password is equal to the one from database or not.

# pgcrypto - encrypt a few columns

billing column, email column, sensitive column

# Resources:

## Storing Passwords

https://rangle.io/blog/how-to-store-user-passwords-and-overcome-security-threats-in-2017/

