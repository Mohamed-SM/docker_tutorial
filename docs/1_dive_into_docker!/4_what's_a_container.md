# 4. What's a Container
the first thing you should do is not to think about it a physical construct in your computer, because it's not, it's more 
like a process or a set of processes that's has a grouping of resources assigned to it. i know it's not clear what i mean 
by that but follow along. because this is the result that we are going to get at the end, and for now we should start
buy a diagram about the operating system:
## The operating system
blow is a basic diagram for the operating system, we see it's contains in the lower layer the hardware (CPU,RAM,HDD)
and above it the [kernel](https://en.wikipedia.org/wiki/Linux_kernel) and at the top we have the applications, now imagine that the application1 wants to read
a file from the hard drive, to do that the application uses the [system call](https://en.wikipedia.org/wiki/System_call) to talk to the [kernel](https://en.wikipedia.org/wiki/Linux_kernel), in the case
to read a file, the [kernel](https://en.wikipedia.org/wiki/Linux_kernel) then takes that command and talks to the hard drive to read the file and give back the result
to the application
<iframe 
frameborder="0" 
style="width:100%;height:663px;" 
src="https://www.draw.io/?lightbox=1&highlight=0000ff&nav=1&title=OS.drawio#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1fZPOo6LxBca7eldvBEtDfyv8d8DqvIa0%26export%3Ddownload">
</iframe>

Now this is clear,let's take a look at another diagram

<iframe frameborder="0" style="width:100%;height:663px;" src="https://www.draw.io/?lightbox=1&highlight=0000ff&nav=1&title=OS%20App%20and%20HDD%20.drawio#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1McpU5MD4bSE5UdlYr64rKuzg1hIk1_0_%26export%3Ddownload"></iframe>

This time we have two application and let's use just the hard drive. so imagine this scenario where the 1st app needs
the dependency and the 2nd app need the same dependency but in an other version, say that you have a database manager
and you don't what to update because you have a lot of data and it's just working fine with you and that database manager
needs an old version the dependency let's say a system library. now you need to use an other program, a browser for 
example, browsers need to be in the latest version for security reasons and this time the browser needs the latest 
version of the same dependency, now we have a problem,

The solution would be [namespacing](https://en.wikipedia.org/wiki/Linux_namespaces) , it's an operating system feature, it's segmenting portions of the system resources
like the hard drive of the RAM, so we can make a segment in the hard drive for each version dependency, then the [kernel](https://en.wikipedia.org/wiki/Linux_kernel)
decides which segment to use when it gets a system call depending on the application that made the system call, and by this
we can have both the browser and the database manager can work at the same time.

Namespacing is used to isolate resources for a process or a group of processes, and this gives is too the ability to
restrict the process for example we can restrict the access to the network or the processes that it can see and talk to

Close to this idea we have also [control groups](https://en.wikipedia.org/wiki/Cgroups) which is similar but in this 
case we condole amount of resources like the limit of the memory that it can allocate or network bandwidth

So the using those two defection we can say that we go back to what is a container and like i said in the first part
of this section: a **container** is a process or a set of processes that's has a grouping of resources assigned to it

<iframe frameborder="0" style="width:100%;height:663px;" src="https://www.draw.io/?lightbox=1&highlight=0000ff&nav=1&title=Copy%20of%20OS%20App%20and%20HDD%20.drawio#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1e7OSdevkgHU8F-M9Bb59wpVPuf-9sxvA%26export%3Ddownload"></iframe>

## Docker container
so to recap a container is a process or a group of precess that when it sends a system call the kernel, The kernel will 
look at that system call and redirect to a specific segment of the hard drive, the network, the memory and the CPU or any
other resource

<iframe frameborder="0" style="width:100%;height:663px;" src="https://www.draw.io/?lightbox=1&highlight=0000ff&nav=1&title=container.drawio#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D11GIDOe7WpfWS5YVqWz9MxTdJj6FJ8RWz%26export%3Ddownload"></iframe> 

## Docker image
the image is a file system snapshot, it's copy of a set of directories and files, plus a startup command,
so the image have the programmes and all there dependencies in it and it has a command that we need to run
when the container is created from that image and stared

<iframe frameborder="0" style="width:100%;height:663px;" src="https://www.draw.io/?lightbox=1&highlight=0000ff&nav=1&title=image%20and%20container.drawio#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1ZnAJYeCoLO_1xxq11Z0KRGqFYvcuQj7w%26export%3Ddownload"></iframe>

## creating a container
whene we create a container we copy the snapshot and we run the startup command, every time we create a new container
from and image

<iframe frameborder="0" style="width:100%;height:583px;" src="https://www.draw.io/?lightbox=1&highlight=0000ff&nav=1&title=creating%20contianers%20from%20image#Uhttps%3A%2F%2Fdrive.google.com%2Fuc%3Fid%3D1iLw45Kcd4MVrYEOzRV9CVBv2GNLUsdcT%26export%3Ddownload"></iframe>

so the kernel will isolate a portion of the hard drive and place in it the snapshot from the image, and then the startup
command is executed and that process is isolated to the set of resources inside the container.

that's the relationship between the image and the container
