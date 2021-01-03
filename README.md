# Docker Cheat Sheet


## References : ##
**Youtube:** <a href="https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=1">
Automation Step by Step - Playlist - Docker
</a>


# Level 1 -> Up and Running : #


## Why Docker? ##
1. **The same behaviour on different devices**  
With docker you can make sure that your code 
will show the same results on different devices and platforms.  
So code will work on the testing environment exactily like
it works on the production environment.
2. **Publish your projects, and use other's projects**  
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

## A: About Docker commands : ##
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


1. **Display docker commands**  
```bash
docker
```
***
2. **Display docker version**   
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
3. **Display docker version with details**   
To display more info about the docker engine, of client and server.
```bash
docker version
```
***
4. **Display information about images and containers**   
```bash
docker info
```
▼<br>
Containers: 1, Running: 1, Paused: 0, Stopped: 0, Images: 1

5. **Help**   
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

5. **Login to docker hub**   
```bash
docker login
```
Now enter username and password, you should have a 
docker hub account created.




## B: Images : ##


