# 3. Using the Docker Client
As we sow the in the last section after installing docker we have ran a command `docker run hello-world`
and the out put was like this:
*output*
```text
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

## What did happen?
in the output we have the text `Hello from Docker!` which is the message from the docker image,
and below it we see the steps that accrued when we ran the command `docker run hello-world`. 

Now back to the top of the output we see `Unable to find image 'hello-world:latest' locally` this means that the image
**hello-world** doesn't exist locally in your hard drive. this is where we start, so what happened is like this:
1. we ran the command `docker run hello-world`, with this we give the **docker-cli** an order to run the image 
**hello-world**
2. the docker client or **docker-cli** issue our command to the **docker-server** to create a container from the 
**hello-world** image and run it

3. the docker checks if this image exist in your machine first, by looking at the **image-cache**, and because we have
 just installed docker the **image-cash** is empty that's why we see the message

```text
Unable to find image 'hello-world:latest' locally
```

4. next the docker server reachs to a service name [**docker-hub**](https://hub.docker.com/) which is a repository
of publicly available free docker images that you can download an run on your computer to download the **hello-world**
image that's what

```text
latest: Pulling from library/hello-world
1b930d010525: Pull complete 
Digest: sha256:4df8ca8a7e309c256d60d7971ea14c27672fc0d10c5f303856d7bc48f8cc17ff
Status: Downloaded newer image for hello-world:latest
```

5. the hello-world image is now stored in the image cache the next thing is creating a container from this image

6. then starting the container

7. and the rest of the output is the output from the container that was created

```text
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

no let's see what happens if when we run the same command for a second time

```bash
docker run hello-world
```

the output is going to be like this:
*output*
```text

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

without the first messages from the docker server because the image exist the docker server will just create a
container and start it
