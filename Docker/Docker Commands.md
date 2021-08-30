-t: add a tag

.: into current directory

```bash
 docker build -t superawesomecontainer .
 docker run -it superawesomecontainer
```

-it: give us TTY environment

<img src="Docker Commands.assets/Screen Shot 2021-08-29 at 7.58.53 PM.png" alt="Screen Shot 2021-08-29 at 7.58.53 PM" style="zoom:50%;" />

"cf26f2005fbc": hash generatered by docker to identify different containers

<img src="Docker Commands.assets/Screen Shot 2021-08-29 at 8.02.13 PM.png" alt="Screen Shot 2021-08-29 at 8.02.13 PM" style="zoom:50%;" />

Now we have the node with version we need.

```bash
 run -it -d superawesomecontainer
```

-d: run on the background

```bash
docker ps
```

Show all container running:

![Screen Shot 2021-08-30 at 2.04.11 PM](Docker Commands.assets/Screen Shot 2021-08-30 at 2.04.11 PM.png)

```bash
 docker exec -it a63cfbb59190 bash
```

above to enter the container again

```bash
 docker stop a63cfbb59190
```

```bash
docker run -it p 3000:3000 superawesomecontainer
```

above bind the port 3000 of the container to the machine port 3000, so that on machine brwoser we can launch the app in the container (with port 3000)

# resource:

More docker commands: https://docs.docker.com/engine/reference/builder/#usage