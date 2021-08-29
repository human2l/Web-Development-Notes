in root folder of project:

```shell
touch Dockerfile
```

Go to https://hub.docker.com, find the tags we need:

<img src="Install Docker.assets/Screen Shot 2021-08-29 at 7.52.54 PM.png" alt="Screen Shot 2021-08-29 at 7.52.54 PM" style="zoom:50%;" />

in Dockerfile:

```dockerfile
//tell docker what node image to use
//parent image
FROM node:8.11.1

//tells us what to run in the container
//"/bin/bash": go into bash profile
CMD ["/bin/bash"]
```

-t: add a tag

.: into current directory

```shell
docker build -t superawesomecontainer .
```

```shell
docker run -it superawesomecontainer
```

-it: give us TTY environment

<img src="Install Docker.assets/Screen Shot 2021-08-29 at 7.58.53 PM.png" alt="Screen Shot 2021-08-29 at 7.58.53 PM" style="zoom:50%;" />

"cf26f2005fbc": hash generatered by docker to identify different containers

<img src="Install Docker.assets/Screen Shot 2021-08-29 at 8.02.13 PM.png" alt="Screen Shot 2021-08-29 at 8.02.13 PM" style="zoom:50%;" />

Now we have the node with version we need.

