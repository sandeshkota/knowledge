### What is Docker ?
 Docker is essentially a toolkit that use OS-level virtualization to deliver software in packages called containers.

### What is Containerization ?
Containers are completely isloated environments i.e. own processors, services, network interfaces, etc. which shares the same OS Kernel.
Multiple containers can run in a single server.

### Architecture
OS contains two layers: Applciation Layer + Kernel Layer  
Docker virtualizes the Application Layer thus using the same Kernel across different containers  
So basically Docker sits on top the OS Kernels and enables the Containerization  

### Containerization v/s Virtualization (VM: Virtual Machine)
Containerization
- Virtualizes only the Applciation Layer
- Smaller Size
- Boot faster
- Less Isolation as the Kernel is shared
  
Virtualization
- Virtualizes both Application and Kernel Layer
- Larger Size
- Boot slower comparitively
- Complete Isolation as the Kernel is virutalized and not shared

![VM v/s Containers](https://s7280.pcdn.co/wp-content/uploads/2018/07/containers-vs-virtual-machines.jpg)

It is not VM v/s Containers. We can have a mixed model.  
Two VMs running on a server and multiple Containers on each VM.

### Docker Image ?
An image is a package or a template. It is used to create one or more containers

### Containers ?
Containers are running instances of images that are isoalted and have own environments and set of processes.

### Benefits of Docker
- Compatibility / Dependency
- Minimizes the Setup time
- Different Dev/Test/Prod environment setup


### Docker Engine
- Docker CLI: Command Line Interface for interacting with user. Uses Rest API to communicate with Docker Daemon
- HTTP API: An API interface used to talk to Daemon and provide instructions 
- Docker Daemon: background process that manages docker object such as images, volumes, network etc..

### Layered Architecture
- Docker creates an image each time a change is applied on the base image
Example: Sample Dockerfile  - which downlaods the Ubuntu  and then installs pyhton etc..
```yaml
FROM UBUNTU

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY ./opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

- Step #1: The OS image is downloaded
- Step #2: Then when python is installed, a new image is created
- Step #3: Then when flask is installed, a new image is created
- Step #4: Then when the source-code is copied, a nwe image is created

Also suppose a step failed, then the after fixing the issue, docker uses the images that are already built and builds images on top of it.  
By doing this when there is an update only in source-code, docker builds the image by taking the already built image from Step #3
