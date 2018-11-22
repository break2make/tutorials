
# Dcoker introduction

## Video Links
- https://www.youtube.com/watch?v=wxxigbHwDGM


# Docker tools

# Dockerfile


# Build docker images

To build a docker image, you need a Dockerfile. It is a best practice to keep the Dockerfile in your present working directory (i.e. the directory from which you are running your docker command in terminal). 

`sudo docker build -t img_name:tag .`

Where “.” is the docker build context. You can use the build context which is different from current directory.  

You might think to use a custom-name for your docker file instead of Dockerfile, and there are different ways to do that.

**Approach 1:** 

`sudo docker build -t img_name:tag - < path-to/Dockerfile_name `

(not recommended as it creates complexity of handling directory path in docker host)

**Approach 2:** 

`sudo docker build -t img_name:tag -f cust_dockerfile_name .`

Note that the location of your dockerfile will be your build context.

In addition, the “docker build” command creates a .tar file of the build context (i.e. the directory of Dockerfille) and send it to docker daemon. So, it is recommended to keep unnecessary information out of this directory; otherwise, the image building will take more time.

Sometime you will find the “docker build” command to use the cached information, and to avoid that you can use “--no-cache” option:

`docker build --no-cache -t img_name:tag -f cust_dockerfile_name .`

In older versions of Docker you needed to pass --no-cache=true, but this is no longer the case.
Save and load images to/from a local file

# Save/Load images to/from local file

To save an image to a local file, you can use the following command:

`sudo docker save -o path-to/img_filename.tar imgname:tag`

However, if you save an image using above command, there might be a permission issue when you try to copy it to external devices, e.g., pendrive. As a remedy to this issue, you can use the following command which does the same job:

`sudo docker save imgname:tag > path-to/img_filename.tar`

Once the image is saved to local file, you might want to get the that image in docker from the *.tar file. \To load the \'image from the *.tar file into the docker local image repo, use the one of the following commands:

Command 1: 

`sudo docker load -i path-to/img_filename.tar`

Command 2:  (it will not create any permission issues)

`sudo docker load < path-to/img_filename.tar`

# Run/Create a container

`sudo docker run -it --rm --network host -v $(pwd)/host_dir_name:absolute-path-to/container_dir img_name:tag command`

Where:\
`--rm`: container is removed upon exit command in container console \
`-it`: for interactive \
`-d`: to detach and run the container in background \
`-v`: to create a volume from command line \
`--network`: for network driver \

# Save a container as docker image


# Transfer file/folder between docker container and host

This can be achieved in two ways: i) docker voulme and ii) docker cp.

## Docker cp
The docker cp command is used for copying files and folders between Docker container and a host machine. 

**Command Usage**

```console
$ sudo docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|- 
$ sudo docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH
```    
 
**Example**

First find the container’s name or ID using the docker ps command:

```console
$ sudo docker ps
CONTAINER ID  IMAGE    COMMAND  CREATED      STATUS      PORTS  NAMES 
72ca2488b353  my_image          X hours ago  Up X hours         my_container`
```

*Copy a file from host to container:* 

```console
$ sudo docker cp foo.txt 72ca2488b353:/foo.txt
```

*Copy a file from Docker container to host:*

```console
$ sudo docker cp 72ca2488b353:/foo.txt foo.txt`
```

For more details, refer to [Docker Documentation](https://docs.docker.com/engine/reference/commandline/cp/)



graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;



# Docker networking

## Video Links
- https://www.youtube.com/watch?v=Xxhhdo2e-DA


# References

[MS-2017:] Containers as the foundation for DevOps collaboration. [[Link]](https://docs.microsoft.com/en-us/dotnet/standard/containerized-lifecycle-architecture/docker-application-lifecycle/containers-foundation-for-devops-collaboration)

[PACK-HUB-2017:] Understanding Container Scenarios and Overview of Docker. [[Links]](https://hub.packtpub.com/understanding-container-scenarios-and-overview-docker/)

[Agarwal-2017] Life Cycle of Docker Containers. [[Link]](https://medium.com/@nagarwal/lifecycle-of-docker-container-d2da9f85959)

[Ramraj-2017] From Docker Images -> Docker Container. [[Link]](https://medium.com/@ramrajchandradevan/from-docker-images-docker-container-b6b042b497a8)

[Rajesh-2018] Lifecycle of Docker Containers. [[Link]](http://www.scmgalaxy.com/tutorials/lifecycle-of-docker-containers/)

[Devhints] Docker CLI cheatsheet. [[Link]](https://devhints.io/docker)

Docker Internals. [[Link]](http://docker-saigon.github.io/post/Docker-Internals/)
