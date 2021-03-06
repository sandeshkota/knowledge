### Docker exits after running unless a process inside the container is running. 
- Running 
```yaml
docker run nginx 
```
will download the image and run the contianer
- Then if you run 
```yaml
docker ps -a 
```
will show the container in exited state
- Ideally containers are meant to run a specific process and not to run the OS

### Run and Sleep for sometime
```yaml
docker run ubuntu sleep 5 
```
runs the container, waits for 5 ms and then exits

### By default Docker doesn't listens to the standard input or output
We need to attach the standard input / output for the container


### Private Registry
- By default docker tries to download the image from docker hub (docker.io)
- If you want the docker to look into your private registry

```yaml
docker login private-registry.io

docker run private-registry.io/apps/internal-app
```
- Docker provides a registry manager as a docker image
```yaml
docker run -d -p 5000:5000 --name registry regiistry:2

docker image tag my-image localhost:5000/my-image

docker push localhost:5000.my-image

docker pull localhost:5000/my-image

docker pull 192.168.56.100:5000/my-image
```


## Namespace PID
As containers runs in host machine and each process must have a unique ID, how does docker run services inside container and manage    
Docker creates the process starting with Process ID as 1, but in actual it has a different process Id in host machine. Docker manages this mapping.   

## cgroups
Used to restrict the usage of resources for a particular container

- restricting max 50% cpu usage
```yaml
docker run --cpus=.5 ubuntu
```

- restricting memory usage for a container
```yaml
docker run --memory=100m ubuntu
```
