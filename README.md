# Docker Cheat Sheet


## References : ##
**Youtube:** <a href="https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=1">
Automation Step by Step - Playlist - Docker
</a><br>
**Youtube:** <a href="https://www.youtube.com/watch?v=wOdrRlz-gQo&list=PLHOC8WGBZWa1zUT2ipvz2woO55TNPahr4&index=1">
TechiTechnions - Playlist - Dockerfile
</a><br>


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



























# Level 4 -> Container Commands: #

## Containers Commands: ##
```bash
docker run <image name>
docker run -it <image name>
docker ps
docker stop <container id>
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
**1. Display information about running containers**   
run ubuntu in one tab, and in the new tab run this command
```bash
docker stats
```
This will be the result:  
▼
<br>
	CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O   PIDS  
	c5cdedbaa437   upbeat_volhard   0.00%     1.805MiB / 2.975GiB   0.06%     1.05kB / 0B   0B / 0B     1




**2. Displaying disk information**   
Sometimes we may want to run a container in an interactive
way, Ubuntu for example.
```bash
docker system df
```
The result:<br>
▼<br>
	TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE<br>
	Images          3         3         100.5MB   0B (0%)<br>
	Containers      5         1         1.142kB   1.142kB (100%)<br>
	Local Volumes   0         0         0B        0B<br>
	Build Cache     0         0         0B        0B<br>



**3. Deleting unused data**  
**BE CAREFUL WHEN USING THIS COMMAND**
```bash
docker system prune
```
This command will delete all the :
1. Stopped containers
2. Dangling images 
(Images not used by at least one container)























# Level 6 -> Dockerfile Simple  : #

## What is the docker file: ##
This is the file that contains the instructions to 
create the docker image


## How to start: ##
**1. Create a file** called **`Dockerfile`** without extensions,
inside the project folder  
	For example, do not call it <del>Dockerfile.txt</del>  
	This is the default name of the docker file  
	You can give it another, but this is the default name  

**2. Fill the dockerfile** with data
	This is an example:
```Dockerfile
#Lines startng with hash are comments

#getting the image to build from
#Here we will start from the "ubuntu" image

FROM ubuntu
```
Save the file and close

**3. Using the CLI (Command Line Interface), change the directory** to 
the directory of the folder of the project that contains the
dockerfile.

**4. run this command** in the CLI 
```bash
docker build .
```
Now you have a new image, that starts from the ubuntu image.  
**Note: this dockerfile is attached to the project, 
and it is called Dockerfile**



















# Level 7 -> Dockerfile  more: #

**1. Create a file** called **`Dockerfile2`** without extensions,
	with the same instructions as the previous example 

**2. Fill the dockerfile** with data
	This is an example:
```Dockerfile
FROM ubuntu
LABEL maintainer_name="My Name"
LABEL maintainer_mail="myname@example.com"
RUN apt-get update
CMD ["echo", "Hello, World!"]
```
- **MAINTAINER**: Telling information about yourself (Optional)
- **RUN** will be executed at the creation of the image
	- This command will update ubuntu to the latest version
- **CMD**  will be executed at the creation of the container

**3. Using the CLI (Command Line Interface), change the directory** to 
the directory of the folder of the project that contains the
dockerfile.

**4. run this command** in the CLI <b>
```bash
docker build -f Dockerfile2 -t testing_image:1.0 .
```
</b>
- **-f Dockerfile2**: specify the dockerfile location
- **-t image_name:image_tag**: 
specify the name of the image, and the tag

**5. Now run the image**
```bash
docker images
#Copy the image id
docker run <image id>
```
It will print **"Hello, World!"**


















# Level 8 -> docker-compose: #

## What is docker-compose: ##
It is a command to run a docker-compose file.  
This enables you to **run lots of docker containers at the same time**.

## docker-compose file language: ##
**YAML** (YAML Ain't Markup Language).  
This is a language **like JSON and XML to store data**.  
It stores data in a **pythonic way**, where what matters the most is 
**spaces and intends**, in stead of curly braces and tags.  
So is has the extension of **.yml**

**1. Create a file** called **`docker-compose.yml`** 
in the project directory 


**2. Fill the dockerfile** with data
	This is an example:<b>
```yaml
version: "1"
services:
  web: 
    image: nginx
    ports:
    - 9090:80
  database: 
    image: redis
```
</b>
**3. Using the CLI (Command Line Interface), change the directory** to 
the directory of the folder of the project that contains the
docker-compose file.

**4. Check** that the file can run, using the CLI, run this code:
```bash
docker-compose config
```
This will be the result
```
Version in ".\docker-compose.yml" is invalid.
You might be seeing this error because you're using the wrong Compose file version.
Either specify a supported version (e.g "2.2" or "3.3")
and place your service definitions under the `services` key,
or omit the `version` key and place your service definitions at the root of 
the file to use version 1.
For more on the Compose file format versions, 
see https://docs.docker.com/compose/compose-file/
```
**5. Fix** the Mistake:
<b>
```yaml
version: "3.8"
services:
  web: 
    image: nginx
    ports:
    - 9090:80
  database: 
    image: redis
```
</b>
Or erase the version.
Now the file is working correctly.

**5. Up and running**:
in the CLI, type this command:<b>
```bash
docker-compose up -d
```
</b>
The <b>d</b> flag to escape the the command line and to write more codes.

Now in the CLI, type this command to display the running containers.
<b>
```bash
docker ps
```
</b>
You will see that the nginx container is running on the port 
the you specified.  

In the browser's adress bar, type this:  
<b>
```bash
127.0.0.1:9090
```
</b>
To end the containers.  

**6. Shut down**:
In the CLi type this command:
<b>
```bash
docker-compose down
```
</b>

**7. Scaling up and down**:
We use the <b>--scale</b> to scale specific services
<b>
```bash
docker-compose up -d --scale database=4
```
</b>

Then:
<b>
```bash
docker-compose up -d --scale database=5
```
</b>

Then:
<b>
```bash
docker-compose up -d --scale database=3
```
</b>
Now we can control the number instances of the image.<br>
This means that we have <b>one redis image, and one nginx image</b>.<br>
But we have:<br>
<b>1 nginx container</b>, and <br>
<b>3 redis containers</b>
















































# Level 9 -> docker volume: #

## What is docker volume: ##
Docker volume is a seperated place for the to store the data.<br>
You can connect between several containers and the same volume.

## Why docker volume: ##
By default, data is stored inside the container.<br>
In production, You can not store the data inside the container.<br>
Because the container can be deleted in case of scaling up and down.<br>
So you have to store the data in a separated place, that should not
be deleted when scaling up or down.<br>
This place is called the volume.<br>
When deleting the container, the volume will not be deleted.



**1. Display docker volume commands**
Inside the CLI, type this command:<b>
```bash
docker volume --help
```
</b>
This will be the result:  
▼<br>

```
Usage:  docker volume COMMAND
Manage volumes
Commands:
  create      Create a volume
  inspect     Display detailed information on one or more volumes
  ls          List volumes
  prune       Remove all unused local volumes
  rm          Remove one or more volumes
Run 'docker volume COMMAND --help' for more information on a command.
```


**2. Create Volumes**
```bash
docker volume create <volume name>
docker volume create volume1
```

**3. Display Volumes**
```bash
docker volume ls
```


































