### Docker has two basic versions
- Community Edition (CE)
- Enterprose Edition (EE)

### On Linux
- Based on type (CentOs, Debian, Fedora, Ubuntu) and its versions 

### On Windows
- Docker Toolbox: Uses **Oracle's Virtual Box** to run Linux and then on top of it installs and runs the docker (Deprecated)
- Docker Desktop: Uses Windows native virtualization known as **Microsoft Hyper-v** to run Linux and then on top of it installs and runs the docker 
- Native support: Base Images - Windows Server Core and Nano Server (only for certain version on windows OS)

### On MacOS
- Docker Toolbox: Uses Oracle bootbox to run Linux and then on top of it installs and runs the docker (Deprecated)
- Docker Desktop: Uses Hyperkit to run Linux and then on top of it installs and runs the docker 

### Container Orchestration Tools: Kubernets (Others - Docker Swarm , MESOS)
Container Orchestration tool. Helps in
- managing containers
- runs many containers of same image in parallel
- failure management. brings up a container in case a container fails and stops
- monitors the container
- etc..

