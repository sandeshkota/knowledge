### Creation of Docker Image

### Pushing Images to Central Repository

### Running Docker Image
docker will run the image by using the below comman. Docker downla=oads the image (if it is not already downloaded) and then runs it.
``` docker run <docker_image_name> ```
docker tries to download the package from dockerhubio
``` docker run nginx ```
in the above example the nginx image is downloaded from [Dockerhub](https://hub.docker.com/_/nginx)  

To just pull the image not to run the container
``` docker pull nnginx ```

### Working with Docker
To list all the containers that are running
``` docker ps ```
To list all containers that are running / stopped / closed
``` docker ps -a ```

To stop a running container
```
docker stop <container_id>
// OR
docker stop <name>
docker stop container_name
```

To clean up a container (permanently)
```
docker rm <name>
docker rm container_name
```

To see the list of download images
``` docker images ```

To remove the downloaded image
```
docker rmi <image_name>
docker rmi nginx
```
