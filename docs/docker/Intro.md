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

![VM v/s Containers](https://i2.wp.com/www.docker.com/blog/wp-content/uploads/Blog.-Are-containers-..VM-Image-1.png)

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
