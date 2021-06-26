After `$npm install` or `$npm update` rpm will show vulnerabilities it founds:

<img src="Keeping Projects Up To Date.assets/Screen Shot 2021-06-26 at 8.58.25 PM.png" alt="Screen Shot 2021-06-26 at 8.58.25 PM" style="zoom:25%;" />

After `$npm audit fix` it might still have vulnerabilities found. Run `$npm audit` will show what might issues are:

<img src="Keeping Projects Up To Date.assets/Screen Shot 2021-06-26 at 9.01.34 PM.png" alt="Screen Shot 2021-06-26 at 9.01.34 PM" style="zoom:25%;" />

`$npm audit fix --force` will force update all dependencies up to date.

In package.json

```json
"dependencies": {
"React":"^16.10.2"
}
```

The symbol "^" means when using `$npm update` it will automatically update "React" to latest version.

