---
title: "Installation of Docker and Portainer"
date: 2022-11-30T13:13:54+06:00
draft: false
searchHidden: false
Description:  In this post I will show how to install docker and portainer in a linux distro.

---
# Installtion of Docker:
The docker package is not available in the default package manager. So we have to add the package in the repo by the following commands: 
1. Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:
``` 
sudo apt-get update 
sudo apt-get install \ 

    ca-certificates \ 

    curl \ 

    gnupg \ 

    lsb-release
```
2. Add Docker’s official GPG key:
``` 
sudo mkdir -p /etc/apt/keyrings 

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg 
```
3. Use the following command to set up the repository:
```
echo \ 

  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \ 

  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
```
\
\
Now the docker package has been installed in the repository. And now we can `download` and `install` Docker. 
```
sudo apt-get update 

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
``` 
\
To check if Docker is installed correctly your can `check` by successfully running the ```hello-world``` image.
```
sudo docker run hello-world
```
# Installing and setting up portainer:
For installing Portainer. We first need to create a volume named portainer_data. 
```
docker volume create portainer_data
```
Then, we need to  download and install the Portainer Server container: 
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
\
\
Portainer Server has now been installed. You can check to see whether the Portainer Server container has started by running `docker ps`:
```
root@server:~# docker ps
CONTAINER ID   IMAGE                                              COMMAND                  CREATED        STATUS        PORTS                                                                                  NAMES
f4ab79732007   portainer/portainer-ee:latest                      "/portainer"             2 weeks ago    Up 29 hours   0.0.0.0:8000->8000/tcp, :::8000->8000/tcp, 0.0.0.0:9443->9000/tcp, :::9443->9443/tcp   portainer
```
Now that the installation is complete, you can log into your Portainer Server instance by opening a web browser and going to:
```
https://localhost:9443
```
If your are connecting to a remote server change `localhost` to relavent ip address.
\
\
### If you want to install portainer in different port:
 Then while installing instead of `-p 9443:9443` type `-p port-of-yourchoice:9443`.
 ```
 docker run -d -p 8000:8000 -p port-of-yourchoice:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
Then you can complete the installation by loging into Portainer Server instance by opening a web browser and going to:
```
https://localhost:9443
```
Done.


# Thanks.