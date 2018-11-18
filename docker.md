
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

To save an image to a local file, you can use the following command:

`sudo docker save -o path-to/img_filename.tar imgname:tag`

However, if you save an image using above command, there might be a permission issue when you try to copy it to external devices, e.g., pendrive. As a remedy to this issue, you can use the following command which does the same job:

`sudo docker save imgname:tag > path-to/img_filename.tar`

Once the image is saved to local file, you might want to get the that image in docker from the *.tar file. To load the image from the *.tar file into the docker local image repo, use the one of the following commands:

Command 1: 

`sudo docker load -i path-to/img_filename.tar`

Command 2:  (it will not create any permission issues)

`sudo docker load < path-to/img_filename.tar`

# Run/Create a container

`sudo docker run -it --rm --network host -v $(pwd)/host_dir_name:absolute-path-to/container_dir img_name:tag command`

Where:
`--rm`: container is removed upon exit command in container console

`-it`: for interactive 

`-d`: to detach and run the container in background

`-v`: to create a volume from command line

`--network`: for network driver 


