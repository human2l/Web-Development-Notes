<img src="index.assets/Screen Shot 2021-10-07 at 2.24.51 PM.png" alt="Screen Shot 2021-10-07 at 2.24.51 PM" style="zoom:50%;" />

## Continuous Integration



### Continuous Delivery



### Continuous Deployment

like GithubPages autodeploy when code changes

## Old way:

<img src="index.assets/Screen Shot 2021-10-07 at 2.31.35 PM.png" alt="Screen Shot 2021-10-07 at 2.31.35 PM" style="zoom:50%;" />

let's say, Friday, where they would then wait and all of them would merge their changes all at once into the master branch.

You would get conflicts and panics before the weekend and people would have to fix their code because they broke other parts of the code.

Now, continuous integration avoids this by having coders make pull requests daily, emerging to master daily.

It's important that developers integrate their changes as soon as possible on the main repository.

If you let the code sitting on the branch or developer workstation for too long, then you expose yourself to this risk of having too many conflicts and all these features now working together.

## Modern way:

<img src="index.assets/Screen Shot 2021-10-07 at 2.35.27 PM.png" alt="Screen Shot 2021-10-07 at 2.35.27 PM" style="zoom:50%;" />

When you merge, once you've tested everything, when you make the pull request to GitHub, GitHub automatically lets a circleci server know, hey, we just have a pull request. Can you run all the tests? Perhaps a run typescript, run lending, run all the tests, make sure everything passes and build the project. If nothing fails in that step, everything is good to go.

<img src="index.assets/Screen Shot 2021-10-07 at 10.28.32 PM.png" alt="Screen Shot 2021-10-07 at 10.28.32 PM" style="zoom:50%;" />

**Staging**:

Staging is kind of like a practice field to make sure that before we send it out to the real world, everything works.

As it's to we can add a process and equal staging environmental variable and we can have some if statements in our code base that says if this is staging, maybe test the speed of our app, how much CPU we're using, if it's connected to the database properly, and you want to mimic the staging as much as you can with production such as having similar databases, similar information, the more the staging has in common with production, the more we can assume that things are going to work. Once we push to production

**Acceptance Test:**

Where perhaps a a tester or a product owner tests on the staging server to make sure everything works, that our new feature works.

**Smoke test:**

So you might want to have for smoke tests, real time monitoring of your production servers to be able to track you regularities or metrics that show that something's not going right. And you have companies not like New Relic that allow you to monitor your service.

# Resources

### CI Tools

There are a lot of good options for tools out there: https://code-maze.com/top-8-continuous-integration-tools/

TravisCI or CircleCI for hosted CI servers. 

Jenkins for your own managed CI servers.

