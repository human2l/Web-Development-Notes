in root folder of project:

```shell
touch Dockerfile
```

Go to https://hub.docker.com, find the tags we need:

<img src="Dockerfile.assets/Screen Shot 2021-08-29 at 7.52.54 PM.png" alt="Screen Shot 2021-08-29 at 7.52.54 PM" style="zoom:50%;" />

in Dockerfile:

```dockerfile
//tell docker what node image to use
//parent image
FROM node:8.11.1

//bash will open in this directory
WORKDIR /usr/src/smart-brain-api

//copy everything of current directory into WORKDIR
COPY ./ ./

//RUN commands are commands used for build our image
RUN npm install

//CMD command is the command executes by default when you launch the build
//ONLY 1 CMD allowed
//tells us what to run in the container
//"/bin/bash": go into bash profile
CMD ["/bin/bash"]
```

