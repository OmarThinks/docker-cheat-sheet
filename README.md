# Docker Cheat Sheet


## References : ##
**Youtube:** <a href="https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=1">
Automation Step by Step - Playlist - Docker
</a><br>
**Youtube:** <a href="https://www.youtube.com/watch?v=wOdrRlz-gQo&list=PLHOC8WGBZWa1zUT2ipvz2woO55TNPahr4&index=1">
TechiTechnions - Playlist - Dockerfile
</a><br>


## Docker commands summary: ##
<b>

```bash
# 1) basic Commands
docker
docker --version
docker -v
docker info
docker --help
docker images --help
docker login

# 2) Image Commands
docker pull < image name>
docker images
docker rmi < image name or id>
docker rmi < image name or id> --force
docker rmi < image name or id> -f

# 3) Container Commands
docker run <image name>
docker run -it <image name>
winpty docker run -it ubuntu
docker ps
docker stop <container id>
docker ps -a
docker start <image id>
docker rm <container id>
docker rm -f <container id>

# 4) System Commands
docker stats
docker system df
docker system prune

# 5) Dockerfile commands
docker build .
docker build -f Dockerfile2 -t testing_image:1.0 .
docker run <image id>


# 6) Docker Compose commands
docker-compose config
docker-compose up -d
docker-compose down
docker-compose up -d --scale <service name>=number of instances
docker-compose up --force-recreate --build -d

# 7) Docker Volume Commands:
docker volume --help
docker volume create <volume name>
docker volume ls
docker volume inspect <volume name>
docker volume prune
docker volume rm <volume name>
docker run --name <image name> -p 8080:8080 -p 50000:50000 -v <volume name>:/var/jenkins_home jenkins
docker run --name MyJenkins1 -p 8080:8080 -p 50000:50000 -v path/to/my/location:/var/jenkins_home jenkins
```
</b>



## Dockerfile example: ##
<b>

```Dockerfile
FROM ubuntu
LABEL maintainer_name="My Name"
LABEL maintainer_mail="myname@example.com"
RUN apt-get update
CMD ["echo", "Hello, World!"]
```
</b>

## Docker-compose example: ##

<b>

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
**Docker Compose** : Used to create docker containers from images  
**Docker Volume** : To store data in separated place




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
<b>
```bash
docker
```
</b>
And you should see a list of docker commands.<br>
If you did not see a list of commands, then you need to troubleshoot
the problem.








# Level 2 -> Basic commands : #
<b>

```bash
docker
docker --version
docker -v
docker info
docker --help
docker images --help
docker login
```
</b>

### 1. Display docker commands ###
<b>

```bash
docker
```
</b>

***
### 2. Display docker version ###
<b>

```bash
docker --version
```
</b>
or 
<b>

```bash
docker -v
```
</b>
▼<br>

```bash
Docker version 20.10.0, build ...
```
***
### 3. Display docker version with details ### 
To display more info about the docker engine, of client and server.<b>
```bash
docker version
```
</b>

***

### 4. Display information about images and containers ###
<b>

```bash
docker info
```
</b>
▼<br>

```bash
Containers: 1, Running: 1, Paused: 0, Stopped: 0, Images: 1
```
### 5. Help ###
<b>

```bash
docker --help
```
</b>
▼<br>
Get a list of the commands, and how to use them<b>

```bash
docker images --help
```
</b>
▼<br>

Learn how to use the **images** order

### 6. Login to docker hub ###
<b>

```bash
docker login
```
</b>
Now enter username and password, you should have a 
docker hub account created.

















# Level 3 -> Images  Commands: #
**Images are the prototypes of the containers.**<br>
You can find a list of images on the <a 
href="https://hub.docker.com/">Docker Hub Website</a>.

## Images Commands: ##
<b>

```bash
docker pull < image name>
docker images
docker rmi < image name or id>
docker rmi < image name or id> --force
docker rmi < image name or id> -f
```
</b>

### 1. Download a new Image ###
Download any image from docker hub<b>
```bash
docker pull <image name>
docker pull ubuntu
```
</b>
This code will download the ubuntu docker image

### 2. Display Installed Docker images ###   
To display a list of images that you have<b>
```bash
docker images
```
</b>
▼<br>

```bash
REPOSITORY        TAG       IMAGE ID       CREATED       SIZE
docker/getting-started   latest    021a1b85e641   3 weeks ago   27.6MB
```

### 3. Remove Image ###   
To remove an existing image<b>

```bash
docker rmi <image name or id>
docker rmi ubuntu
```

</b>
This code will uninstall the ubuntu docker image.  
Now when we run <code><b>docker images</b></code> 
you will notice that 
the ubuntu mage has been removed.<b>

```bash
docker rmi ubuntu --force
```

</b>
or<b>

```bash
docker rmi ubuntu -f
```
</b>

This will force the image removal.



























# Level 4 -> Container Commands: #

## Containers Commands: ##

<b>

```bash
docker run <image name>
docker run -it <image name>
winpty docker run -it ubuntu 
docker ps
docker stop <container id>
docker ps -a
docker start <container id>
docker rm <container id>
docker rm -f <container id>
```
</b>

### 1. Create a Docker Container ###
To create an image from a container  

<b>

```bash
docker run <image name>
docker run ubuntu
```
</b>
If the image name (Ubuntu in this example) was not
 pulled, it will be pulled and run.

### 2. running interactively ###   
Sometimes we may want to run a container in an interactive
way, Ubuntu for example.
<b>

```bash
docker run -it <image name>
docker run -it ubuntu 
```
</b>
On Windows:
<b>

```bash
winpty docker run -it ubuntu 
```
</b>
Try these commands:
<b>

```bash
ls
exit 
```
</b>
Now we are running the ubuntu command line.<br>
If you face any problem on windows, follow up here:<br>
<a href="https://stackoverflow.com/questions/60875207/docker-oci-runtime-create-failed-container-linux-go349-starting-container-pro">https://stackoverflow.com/questions/60875207/docker-oci-runtime-create-failed-container-linux-go349-starting-container-pro</a>


### 3. Display Containers ###  
This commands will display the containers.  
Now run ubuntu in a tab, and run this this command in a new tab.
<b>

```bash
docker ps
```
</b>

This code will display info about containers like this:  
```bash
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
a115a0df6e43   ubuntu    "/bin/bash"   2 minutes ago   Up 2 minutes             priceless_colden
```
As we can see, the ubuntu image is running.  


### 4. Stop a Container ###   
To remove an existing image
<b>

```bash
docker stop <container id>
```
</b>

run **`docker ps`** to get the id of the ubuntu container running in 
the first tab.  
and in the the tab
run **`docker stop <ubuntu container id>`**  
It will automatically shut down the ubuntu terminal in the first tab.


### 5. What does it mean to stop a container ###   
This command <b>`docker ps` will only display the running containers.</b>
<br>
When a conatiner stops, t doesn't mean that it has been deleted, it 
just has been stopped.<br>
This command will display all the containers, even the stopped containers.

<b>

```bash
docker ps -a
```
</b>
This result may look like:

```bash
CONTAINER ID   IMAGE          COMMAND                  CREATED      STATUS                     PORTS                  NAMES
4e4bf85b5573   redis          "docker-entrypoint.sΓÇª"   2 days ago   Up 33 minutes              6379/tcp               docker-cheat-sheet_database_3
69f54ecb54de   redis          "docker-entrypoint.sΓÇª"   2 days ago   Exited (255) 2 hours ago   6379/tcp               docker-cheat-sheet_database_2

```

We can differentiate between them from the **STATUS**.<br>
**- Excited:** Stopped Container<br>
**- Up:** The container is running



### 6. Running a stopped container ###   
<b>

```bash
docker start <container id>
docker start 69f54ecb54de
```
</b>
Now, after running `docker ps -a`, the result will look like:

```bash
CONTAINER ID   IMAGE          COMMAND                  CREATED      STATUS                     PORTS                  NAMES
4e4bf85b5573   redis          "docker-entrypoint.sΓÇª"   2 days ago   Up 52 minutes              6379/tcp               docker-cheat-sheet_database_3
69f54ecb54de   redis          "docker-entrypoint.sΓÇª"   2 days ago   Up About a minute          6379/tcp               docker-cheat-sheet_database_2
```
We can differentiate between them from the **STATUS**.<br>
**- Excited:** Stopped Container<br>
**- Up:** The container is running


### 7. Deleting a container ###   
<b>

```bash
docker rm <container id>
```
</b>


### 8. Deleting a running container ###   
<b>

```bash
docker rm -f <container id>
```
</b>

The **-f** flag is to force the container removal.















# Level 5 -> System Commands : #

## Containers Commands: ##

<b>

```bash
docker stats
docker system df
docker system prune
```
</b>

### 1. Display information about running containers ###   
run ubuntu in one tab, and in the new tab run this command

<b>

```bash
docker stats
```
</b>

This will be the result:  
▼
<br>
```bash
CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O   PIDS  
c5cdedbaa437   upbeat_volhard   0.00%     1.805MiB / 2.975GiB   0.06%     1.05kB / 0B   0B / 0B     1
```



### 2. Displaying disk information ###   
Sometimes we may want to run a container in an interactive
way, Ubuntu for example.
<b>
```bash
docker system df
```
</b>
The result:<br>
▼<br>

```bash
TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          3         3         100.5MB   0B (0%)
Containers      5         1         1.142kB   1.142kB (100%)
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
```

### 3. Deleting unused data ###  
**BE CAREFUL WHEN USING THIS COMMAND**
<b>
```bash
docker system prune
```
</b>

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
<b>
```Dockerfile
#Lines startng with hash are comments

#getting the image to build from
#Here we will start from the "ubuntu" image

FROM ubuntu
```
</b>
Save the file and close

**3. Using the CLI (Command Line Interface), change the directory** to 
the directory of the folder of the project that contains the
dockerfile.

**4. run this command** in the CLI 

<b>

```bash
docker build .
```
</b>

Now you have a new image, that starts from the ubuntu image.  
**Note: this dockerfile is attached to the project, 
and it is called Dockerfile**



















# Level 7 -> Dockerfile  more: #

**1. Create a file** called **`Dockerfile2`** without extensions,
	with the same instructions as the previous example 

**2. Fill the dockerfile** with data
	This is an example:

<b>

```Dockerfile
FROM ubuntu
LABEL maintainer_name="My Name"
LABEL maintainer_mail="myname@example.com"
RUN apt-get update
CMD ["echo", "Hello, World!"]
```
</b>

- **MAINTAINER**: Telling information about yourself (Optional)
- **RUN** will be executed at the creation of the image
	- This command will update ubuntu to the latest version
- **CMD**  will be executed at the creation of the container

**3. Using the CLI (Command Line Interface), change the directory** to 
the directory of the folder of the project that contains the
dockerfile.

**4. run this command** in the CLI 
<b>
```bash
docker build -f Dockerfile2 -t testing_image:1.0 .
```
</b>

- **-f Dockerfile2**: specify the dockerfile location
- **-t image_name:image_tag**: 
specify the name of the image, and the tag

### 5. Now run the image ###
<b>

```bash
docker images
#Copy the image id
docker run <image id>
```
</b>

It will print **"Hello, World!"**



### 6. Understand COPY ###
<b>

```dockerfile
COPY src ["path/from", "path/to"]
```
</b>

This command copies from the original folder to the folder of image

















# Level 8 -> docker-compose: #

## docker-compose Commands: ##
<b>

```bash
docker-compose config
docker-compose up -d
docker-compose down
docker-compose up -d --scale <service name>=number of instances
docker-compose up --force-recreate --build -d
```
</b>



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


### 2. Fill the docker-compose ###
This is an example:
<b>

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

9090:80=> This means that 

<b>

```
expose the port 80 in nginx, on port 9090 on my server
```
</b>

**3. Using the CLI (Command Line Interface), change the directory** to 
the directory of the folder of the project that contains the
docker-compose file.

**4. Check** that the file can run, using the CLI, run this code:
<b>

```bash
docker-compose config
```

</b>
This will be the result

```bash
Version in ".\docker-compose.yml" is invalid.
You might be seeing this error because you're using the wrong Compose file version.
Either specify a supported version (e.g "2.2" or "3.3")
and place your service definitions under the `services` key,
or omit the `version` key and place your service definitions at the root of 
the file to use version 1.
For more on the Compose file format versions, 
see https://docs.docker.com/compose/compose-file/
```

### **5. Fix** the Mistake: ###

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

### 6. Up and running ###
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

### 7. Shut down ###

In the CLi type this command:

<b>

```bash
docker-compose down
```
</b>

### 8. Scaling up and down ###
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




### 9. Making edits ###

When you edit the original code, and want to make an image and 
run a container after making the edits, you don't have to 
remove the image and the container. You can simply run these commands:
<b>
```bash
docker-compose up --force-recreate --build -d
```
</b>








































# Level 9 -> docker volume: #

## docker volume Commands: ##
<b>

```bash
docker volume --help
docker volume create <volume name>
docker volume ls
docker volume inspect <volume name>
docker volume prune
docker volume rm <volume name>
docker run --name <image name> -p 8080:8080 -p 50000:50000 -v <volume name>:/var/jenkins_home jenkins
docker run --name MyJenkins1 -p 8080:8080 -p 50000:50000 -v path/to/my/location:/var/jenkins_home jenkins
```
</b>


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



### 1. Display docker volume commands ###
Inside the CLI, type this command:<b>
```bash
docker volume --help
```
</b>
This will be the result:  
▼<br>

```bash
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


### 2. Create Volumes ###
<b>

```bash
docker volume create <volume name>
docker volume create volume1
```
</b>

### 3. Display Volumes ###
<b>

```bash
docker volume ls
```
</b>

### 4. Display Volume Details ###
<b>

```bash
docker volume inspect <volume name>
docker volume inspect volume1
```
</b>
This will be the result:  
▼<br>

```JSON
[
    {
        "CreatedAt": "2021-01-09T09:43:11Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/volume1/_data",
        "Name": "volume1",
        "Options": {},
        "Scope": "local"
    }
]
```

### 5. Remove unused volumes ###
<b>

```bash
docker volume prune
```
</b>
This will remove all the volumes not connected 
with at least one container.

### 6. Remove specific volume ###
<b>

```bash
docker volume rm <volume name>
docker volume rm volume1
```
</b>
This will remove this specific volume.


### 7. Connecting a docker container to a specific volume ###
This is an example of connecting a jenkins container to a volume.<br>
You can fimd this example on docker hub, jenkins image.
<b>

```bash
docker run --name MyJenkins1 -p 8080:8080 -p 50000:50000 -v volume1:/var/jenkins_home jenkins
```
</b>

This will create a docker container called **MyJenkins1** and connect it to the volume.


### 8. Bind Mounts ###
In stead of using a volume, you can use a physical location.
<b>

```bash
docker run --name MyJenkins1 -p 8080:8080 -p 50000:50000 -v path/to/my/location:/var/jenkins_home jenkins
```
</b>



































<!--
# Level 10 -> docker swarm: #

## What is docker swarm: ##
Docker swarm is a way run and manage several containers.<br>
AKA: orchestration.<br>
There is an other way to do the same thing, that is using 
**Kubernetes**.

## Why docker Swarm: ##
1. Containers health check
2. Ensure all containers are up on every system
3. Scaling the containers up and down depending on load
4. adding updates and changes to all the containers

### 1. Validate that docker machine is intalled
In the CLI type this code:
<b>
```bash
docker-machine -v
```
</b>
Result:

```bash
docker-machine.exe version 0.16.0, build 702c267f
```
If you recieved an error, then probably docker machine is not installed
on your device.<br>
You may need to install.<br>
Search on google "Install docker machine".



-->
