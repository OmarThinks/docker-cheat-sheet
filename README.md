# Docker Cheat Sheet


## References : ##
**Youtube:** <a href="https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=1">
Automation Step by Step - Playlist - Docker
</a>


# Level 1 -> Up and Running : #


## Why Docker? ##
**1. The same behaviour on different devices**  
With docker you can make sure that your code 
will show the same results on different devices and platforms.  
So code will work on the testing environment exactily like
it works on the production environment.
**2. Publish your projects, and use other's projects**  
When a project is published on dockerhub, you can pull it easily  
also others can pull your projects

## Definitions : ##

**Docker Image**: the blueprint of the code, or the original code  
**Docker Container**: the runtime instance of the Docker image  
In real like, this looks like cars factory.  
**Docker Image** = **Car Factory**  
**Docker Container** = **Cars**  
There can be lots of cars, but we have a single car factory.  
And there can be **lots of** runtime **docker containers**
, but there can 
only be a **single Docker Image** for similar docker containers.   
**Dockerhub**: https://hub.docker.com/  
	a place to publish docker images, and 
use published docker images.  
**DockerFile** : Used to create docker images




## Installing Docker : ##

- **On Linux:** <a href="https://www.youtube.com/watch?v=KCckWweNSrM&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=5">
Youtube - Automation Step by Step - Playlist - Docker - Install
on Linux
</a>  
- **On Windows:** <a href="https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=6">
Youtube - Automation Step by Step - Playlist - Docker - Install
on Windows</a>  
- **On Mac:** <a href="https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=7">
Youtube - Automation Step by Step - Playlist - Docker - Install
on Mac</a>


## Validation : ##
In the command line (I am using Git-Bash on Windows for example)

Run this command:
```bash
docker
```
And you should see a list of docker commands.  
If you did not see a list of commands, then you need to troubleshoot
the problem.








# Level 2 -> Basic commands : #

```bash
docker
docker --version
docker -V
docker version
docker info
docker help
docker images --help
docker login
```

**1. Display docker commands**  
```bash
docker
```
***
**2. Display docker version**   
```bash
docker --version
```
or
```bash
docker -V
```
▼<br>
Docker version 20.10.0, build ...

***
**3. Display docker version with details**   
To display more info about the docker engine, of client and server.
```bash
docker version
```
***
**4. Display information about images and containers**   
```bash
docker info
```
▼<br>
Containers: 1, Running: 1, Paused: 0, Stopped: 0, Images: 1

**5. Help**   
```bash
docker help
```
▼<br>
Get a list of the commands, and how to use them
```bash
docker images --help
```
▼<br>
Learn how to use the **images** order

**6. Login to docker hub**   
```bash
docker login
```
Now enter username and password, you should have a 
docker hub account created.

















# Level 3 -> Images  Commands: #
**Images are the prototypes of the containers.**<br>
You can find a list of images on the <a 
href="https://hub.docker.com/">Docker Hub Website</a>.

## Images Commands: ##
```bash
docker pull <image name>
docker images
docker rmi <image name or id>
docker rmi <image name or id> --force
docker rmi <image name or id> -f

```

**1. Download a new Image**   
Downlaod any image from docker hub
```bash
docker pull <image name>
docker pull ubuntu
```
This code will download the ubuntu docker image

**2. Display Installed Docker images**   
To display a list of images that you have
```bash
docker images
```
▼<br>
	REPOSITORY        TAG       IMAGE ID       CREATED       SIZE<br>
	docker/getting-started   latest    021a1b85e641   3 weeks ago   27.6MB

**3. Remove Image**   
To remove an existing image
```bash
docker rmi <image name or id>
docker rmi ubuntu
```
This code will uninstall the ubuntu docker image.  
Now when we run **`docker images`** you will notice that 
the ubuntu mage has been removed.
```bash
docker rmi ubuntu --force
```
or
```bash
docker rmi ubuntu -f
```
This will force the image removal.



























# Level 4 -> Container Commands Commands: #

## Containers Commands: ##
```bash
docker images
docker pull <image name>
docker rmi <image name>
docker rmi <image name> --force
docker rmi <image name> -f

```
**1. Create a Docker Container**   
To create an image from a container  

```bash
docker run <image name>
docker run ubuntu

```
If the image name (Ubuntu in this example) was not
 pulled, it will be pulled and run.

**2. running interactively**   
Sometimes we may want to run a container in an interactive
way, Ubuntu for example.
```bash
docker run -it <image name>
docker run -it ubuntu 
```
On Windows:
```bash
winpty docker run -it ubuntu 
```
Try these commands:
```bash
ls
exit 
```
Now we are running the ubuntu command line.<br>
If you face any problem on windows, follow up here:<br>
<a href="https://stackoverflow.com/questions/60875207/docker-oci-runtime-create-failed-container-linux-go349-starting-container-pro">https://stackoverflow.com/questions/60875207/docker-oci-runtime-create-failed-container-linux-go349-starting-container-pro</a>


**3. Display Containers**  
This commands will display the containers.  
Now run ubuntu in a tab, and run this this command in a new tab.
```bash
docker ps
```
This code will display info about containers like this:  
	CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
	a115a0df6e43   ubuntu    "/bin/bash"   2 minutes ago   Up 2 minutes             priceless_colden

As we can see, the ubuntu image is running.  


**4. Stop a Container**   
To remove an existing image
```bash
docker stop <container id>
```
run **`docker ps`** to get the id of the ubuntu container running in 
the first tab.  
and in the the tab
run **`docker stop <ubuntu container id>`**  
It will automatically shut down the ubuntu terminal in the first tab.



















# Level 5 -> System Commands : #

## Containers Commands: ##
```bash
docker images
docker pull <image name>
docker rmi <image name>
docker rmi <image name> --force
docker rmi <image name> -f

```
**1. Create a Docker Container**   
To create an image from a container  

```bash
docker run <image name>
docker run ubuntu

```
If the image name (Ubuntu in this example) was not
 pulled, it will be pulled and run.

**2. running interactively**   
Sometimes we may want to run a container in an interactive
way, Ubuntu for example.
```bash
docker run -it <image name>
docker run -it ubuntu 
```
On Windows:
```bash
winpty docker run -it ubuntu 
```
Try these commands:
```bash
ls
exit 
```
Now we are running the ubuntu command line.<br>
If you face any problem on windows, follow up here:<br>
<a href="https://stackoverflow.com/questions/60875207/docker-oci-runtime-create-failed-container-linux-go349-starting-container-pro">https://stackoverflow.com/questions/60875207/docker-oci-runtime-create-failed-container-linux-go349-starting-container-pro</a>


**3. Display Containers**  
This commands will display the containers.  
Now run ubuntu in a tab, and run this this command in a new tab.
```bash
docker ps
```
This code will display info about containers like this:  
	CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
	a115a0df6e43   ubuntu    "/bin/bash"   2 minutes ago   Up 2 minutes             priceless_colden

As we can see, the ubuntu image is running.  


**4. Stop a Container**   
To remove an existing image
```bash
docker stop <container id>
```
run **`docker ps`** to get the id of the ubuntu container running in 
the first tab.  
and in the the tab
run **`docker stop <ubuntu container id>`**  
It will automatically shut down the ubuntu terminal in the first tab.























































