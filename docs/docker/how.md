### Creation of Docker Image
A docker image is created by using a base image. 
The image is created using the Dockerfile below
```
FROM UBUNTU

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY ./opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

To build an image
```
docker build Dockerfile -t sk/sample-web-app
```

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

### Run - attach and detach
Running a container in attach mode will make the command window attached to that process and cannot be used without stopping the container
``` docker run sk/sample-image ```

Running a container in detach mode will run the container in the background
``` docker run -d sk/sample-image ```

### Running multiple Versions
Running latest version
``` docker run redis ```

Running a sepcific version
``` docker run redis:4.0 ```

Running multiple versions in the same machine
``` docker run redis ``` and ``` docker run redis:4.0 ``` runs both the versions.

### Running a web application
To run a web application by configuring the ports.
``` 
docker run -p 80:5000 sk/web-image 
docker run -p 8001:5001 sk/web-image 
```

### Mouting the Volume
By default the container writes the data in it'w own isoalted environment. And when the container fails or stops, even the data gets deleted.
So to ensure that the data is persisted even when a container stops, we need to map a colume drive while running a container
``` docker run -v /opt/data/datadir:/var/lib/mysql mysql ```

### Other Information
To check information on a container
``` docker inspect  <container_name> ```

To see the logs which we ran in the background
``` docker logs <container_name> ```

## Environment Variables
To use a environment variable 
```
// example in python
os.environ,get('APP_COLOR');
```

To set a enviornment variable while running
``` docker run -e APP_COLOR=blue sk/sample-web-app ```


