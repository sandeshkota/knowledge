### Creation of Docker Image
A docker image is created by using a base image. 
The image is created using the Dockerfile below
```yaml
FROM UBUNTU

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY ./opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

To build an image
```yaml
docker build Dockerfile -t sk/sample-web-app
```

### Pushing Images to Central Repository

### Running Docker Image
docker will run the image by using the below comman. Docker downla=oads the image (if it is not already downloaded) and then runs it.
```yaml
docker run <docker_image_name> 
```

docker tries to download the package from dockerhubio
``` yaml
docker run nginx 
```
in the above example the nginx image is downloaded from [Dockerhub](https://hub.docker.com/_/nginx)  

To just pull the image not to run the container
```yaml
docker pull nnginx 
```

### Working with Docker
To list all the containers that are running
```yaml 
docker ps 
```

To list all containers that are running / stopped / closed
```yaml 
docker ps -a 
```

To stop a running container
```yaml
docker stop <container_id>
// OR
docker stop <name>
docker stop container_name
```

To clean up a container (permanently)
```yaml
docker rm <name>
docker rm container_name
```

To see the list of download images
```yaml 
docker images 
```

To remove the downloaded image
```yaml
docker rmi <image_name>
docker rmi nginx
```

### Run - attach and detach
Running a container in attach mode will make the command window attached to that process and cannot be used without stopping the container
```yaml 
docker run sk/sample-image 
```

Running a container in detach mode will run the container in the background
```yaml
docker run -d sk/sample-image
```

### Running multiple Versions
Running latest version
```yaml
docker run redis 
```

Running a sepcific version
```yaml 
docker run redis:4.0 
```

Running multiple versions in the same machine
```yaml 
docker run redis 
``` 
and
```yaml 
docker run redis:4.0 
```
runs both the versions.

### Running a web application
To run a web application by configuring the ports.
``` yaml
docker run -p 80:5000 sk/web-image 
docker run -p 8001:5001 sk/web-image 
```

### Mouting the Volume
By default the container writes the data in it'w own isoalted environment. And when the container fails or stops, even the data gets deleted.
So to ensure that the data is persisted even when a container stops, we need to map a colume drive while running a container
```yaml
docker run -v /opt/data/datadir:/var/lib/mysql mysql 
```

### Other Information
To check information on a container
```yaml
docker inspect  <container_name> 
```

To see the logs which we ran in the background
```yaml
docker logs <container_name> 
```

To access a container's terminal
```yaml
docker exec -it <container_name> 
```

To Restart
```yaml
docker stop <container_name>
docker start <container_name>
```

## Environment Variables
To use a environment variable 
```yaml
// example in python
os.environ,get('APP_COLOR');
```

To set a enviornment variable while running
```yaml
docker run -e APP_COLOR=blue sk/sample-web-app 
```


