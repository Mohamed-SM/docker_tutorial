# 1. What is docker & Why use it ?
The two most important questions are 
- What is docker ?
- Why use docker ?

Let's start buy why use docker
## Why use docker ?
The normal flow of installing software on your computer

1. Download installer
2. Run installer
3. Get an error message in the installation process
4. Troubleshoot issue
5. Rerun installer
6. Get an other error
7. Repeat from step 4 until the installation succeed

This is what docker is trying ot fix, Docker wants to make it really easy and really straightforward for you to install and run software on
any given computer.

**let's see an example:**
if you go the the official website of redis and then to the download page and take
a look at the installation process it's will ask you to download the tar ball then 
extract it and then compile it and more ....

![](../_media/Screenshot%20from%202019-11-22%2013-59-03.png)

and if you find an error along the way you will have to google it and then try again and again,
i mean do you want to really go throw all of that in stead of running just one command using docker

```bash
docker run -it redis
```
this command will download redis and in just few seconds you will have an instance of it 
ready and running

*output*
```bash
Unable to find image 'redis:latest' locally
latest: Pulling from library/redis
8d691f585fa8: Pull complete 
8ccd02d17190: Pull complete 
4719eb1815f2: Pull complete 
c1d551322836: Pull complete 
e784cd6df1d1: Pull complete 
22d991b147be: Pull complete 
Digest: sha256:be610493a65135fc7e434ebe268a6e2ef384b09505d47080fb1344600562aeb7
Status: Downloaded newer image for redis:latest
1:C 22 Nov 2019 12:55:29.952 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 22 Nov 2019 12:55:29.952 # Redis version=5.0.7, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 22 Nov 2019 12:55:29.952 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
                _._                                                  
           _.-``__ ''-._                                             
      _.-``    `.  `_.  ''-._           Redis 5.0.7 (00000000/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._                                   
 (    '      ,       .-`  | `,    )     Running in standalone mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 6379
 |    `-._   `._    /     _.-'    |     PID: 1
  `-._    `-._  `-./  _.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |           http://redis.io        
  `-._    `-._`-.__.-'_.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |                                  
  `-._    `-._`-.__.-'_.-'    _.-'                                   
      `-._    `-.__.-'    _.-'                                       
          `-._        _.-'                                           
              `-.__.-'                                               

1:M 22 Nov 2019 12:55:29.957 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 22 Nov 2019 12:55:29.957 # Server initialized
1:M 22 Nov 2019 12:55:29.957 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 22 Nov 2019 12:55:29.957 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
1:M 22 Nov 2019 12:55:29.957 * Ready to accept connections

```

it's that simple that's why you should use docker.

## What is docker ?
this question is more complicated to answer, most people when they talk about docker, they are probably talking about 
the hole ecosystem from projects and tools and software:
 - docker client
 - docker server
 - docker machine
 - docker image
 - docker hub
 - docker compose
 
all of these are tools and peaces of software that are been used to create what we call **docker container**. and now
your question is what is a container ?, and all this website is made to answer that question and a bit more like 
creating the containers and using them and more.

lat's take a moment and go back to the previous command that we used to install **redis** `docker run -it redis`, this 
command have done some work behind the seen, now in simple terms by running that command something called **docker cli**
used the **docker hub** and downloaded a file called **docker image**,

### docker image:
the image is a file containing all the
dependencies needed and all the configuration required for a specific program to work in this case that was **redis**.
this image is used to create a **container** 
### docker container: 
the container is an instance of an image, it's like a program with it's own memory
space and and hard drive space and also a networking components


So whe still didn't get into what docker is but we now know about what an image is and what a container is, these two
peaces are what we are going to be working with all the time from now on and we will be going throw more to find about 
how docker works and what it is.
