# 1. installing docker
even thaw we didn't answer the question what is docker? we going to be installing docker it's made of tow parts called the **docker cli**
and **docker server** 

**docker client:**
is the tool we interact it with and issue commands to to use docker

**docker server:**
is the actual peace of software that creates the containers and the images, running and stopping the containers, 
uploading the images and everything else docker is meant to do

## Step 1 : installing docker in Ubuntu
In Ubuntu the documentation on installing docker is [here](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and
for other distributions or operating systems [go here](https://docs.docker.com/install/)

I will be using Ubuntu and the first thing to do is:
1. if for some reason you already have docker, you need to remove it 
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```
it's ok if this reports that the packages are not installed

2. installing prerequisite packages
``` bash
sudo apt update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
3. add the GPG key for the official Docker repository and adding the Docker repository to APT sources

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt update
```
> for ubuntu 19.10 use in the second command this instead 
```bash
sudo add-apt-repository    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   disco \
   stable"
```

Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:

```bash
apt-cache policy docker-ce
```
*output*
```
docker-ce:
  Installed: (none)
  Candidate: 18.03.1~ce~3-0~ubuntu
  Version table:
     18.03.1~ce~3-0~ubuntu 500
        500 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages
```

4. Finally, install Docker:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

and that should be it.
> if you have any problems with the installation leave a comment below

Now let's see if the docker service is running

```bash
sudo systemctl status docker
```
*output*

```
● docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2018-07-05 15:08:39 UTC; 2min 55s ago
     Docs: https://docs.docker.com
 Main PID: 10096 (dockerd)
    Tasks: 16
   CGroup: /system.slice/docker.service
           ├─10096 /usr/bin/dockerd -H fd://
           └─10113 docker-containerd --config /var/run/docker/containerd/containerd.toml

```

## Step 2: add the user to docker group
this step is to avoid running docker with sudo command every time, so just  run 
```bash
sudo usermod -aG docker USERNAME
```
change the `USERNAME` with your user name, and then logout and log in again.
## Step 3: using docker

the first docker image that we should be working with is the **hello-world** image, so to run this image
use the command
```bash
docker run hello-world
```
you should see this output

*output*
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete 
Digest: sha256:4df8ca8a7e309c256d60d7971ea14c27672fc0d10c5f303856d7bc48f8cc17ff
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

if you get an output similar to this that means that everything is working fine and you should be able to follow along 
with us.
