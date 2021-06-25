<img src="Critical Render Path optimization.assets/Screen Shot 2021-06-25 at 6.47.20 PM.png" alt="Screen Shot 2021-06-25 at 6.47.20 PM" style="zoom:30%;" />

<img src="Critical Render Path optimization.assets/Screen Shot 2021-06-25 at 7.21.38 PM.png" alt="Screen Shot 2021-06-25 at 7.21.38 PM" style="zoom:33%;" />

* Load css as soon as possible, JS as late as possible. Because JS requires html and css parsing to finish before it can be run. So, put css link to the front of html page, js link to the bottom of html page right before \</body>

* Load whatever above the fold: prior load what user's eyes can see

<img src="Critical Render Path optimization.assets/Screen Shot 2021-06-25 at 7.08.03 PM.png" alt="Screen Shot 2021-06-25 at 7.08.03 PM" style="zoom: 33%;" />

<img src="Critical Render Path optimization.assets/Screen Shot 2021-06-25 at 7.07.09 PM.png" alt="Screen Shot 2021-06-25 at 7.07.09 PM" style="zoom:25%;" />

* Less specificity: more infomation give to browser, slower it runs

<img src="Critical Render Path optimization.assets/Screen Shot 2021-06-25 at 7.14.08 PM.png" alt="Screen Shot 2021-06-25 at 7.14.08 PM" style="zoom:33%;" />